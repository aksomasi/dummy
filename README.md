
	@PostMapping(value = "/validateAddress")
	   public ResponseEntity<?> validateAddress(@RequestBody  AddressValidationRequest
	     request) {
		 boolean isValid = true;
		 String mycountry = "";
		 int size = 0;
		 String error_message = "";
		 
		 try {

	    		DataQualityServiceStub service = new DataQualityServiceStub(PropertyLibrary.check_address_web_service_url);
	    		CleanAddressRequest cRequest = new CleanAddressRequest();
	    		CleanAddressResponse resp = null;
	    		DQAddress address = new DQAddress();
	    		address.setCity(request.getCity());
	    		address.setStateProvince(request.getState());
	    		address.setZipCode(request.getZip());
	    		address.setLine1(request.getStreetln1());
	    		if (null != streetln2)
	    			address.setLine2(request.getStreetln2());
	    		address.setCountry(request.getCountry());
	    		cRequest.setAddress(address);
	    		cRequest.setNumSuggestions(2);
	    		cRequest.setIsTest(false);
	    		// Axis Wrappers
	    		DataQualityServiceStub.Execute exe = new DataQualityServiceStub.Execute();
	    		exe.setRequest(cRequest);
	    		ExecuteResponse exeResp = service.execute(exe);

	    		// Cast the generic DataQualityResponse to expected response.
	    		resp = (CleanAddressResponse) exeResp.getExecuteResult();

	    		if ( resp != null && resp.getError() != null && null == resp.getError().getMessage()) {
	    			isValid = true;
	    		} else {
	    			if ( resp != null && resp.getError() != null && resp.getError().getMessage().indexOf("addresses found") > 0) {
	    				isValid = false;
	    				
	    			}
	    			if (resp != null && resp.getError() != null && resp.getError().getMessage()
	    					.indexOf("no active subscriptions") > 0) {
	    				isValid = false;

	    			} 
	    			if (null == resp.getError()) {
	    				isValid = false;

	    			} else {
	    				size = resp.getNumSuggestions();
	    			}

	    		}
	    		
	    		if (resp.getAddresses() != null && resp.getAddresses().getDQAddress() == null) {
	    			isValid = false;
	    		}
	    		
	    		 if ( ! resp.getIsZipValid())
	    		 {
	    			 error_message = "The zip code is not valid" ;
	    		 }
	    	
	    		if (isValid) {
	    			
	    			mycountry = resp.getAddresses().getDQAddress()[0].getCountry();

	    			if ( mycountry != null )
	    				mycountry = mycountry.toUpperCase().trim()  ;
	    			else
	    				mycountry = "";
	    		//	if ( mycountry.trim().length() == 0  )
	    		//		mycountry = "United States";
	    				
	    			String address2 = resp.getAddresses().getDQAddress()[0].getLine2()==null ? "": resp.getAddresses().getDQAddress()[0].getLine2();
	    			}

	    		} catch(AxisFault e) {
	    		isValid = false;
	    		e.printStackTrace();
	    		System.out.println(e);
	    	}

	return ResponseEntity.ok("Saved data into Kinessis sucessfully!");
}

////////////////
public class AddressValidationRequest {

	private String streetln1;
	private String streetln2;
	private String city;
	private String state;
	private String zip;
	private String country;
	
	public String getStreetln1() {
		return streetln1;
	}
	public void setStreetln1(String streetln1) {
		this.streetln1 = streetln1;
	}
	public String getStreetln2() {
		return streetln2;
	}
	public void setStreetln2(String streetln2) {
		this.streetln2 = streetln2;
	}
	public String getCity() {
		return city;
	}
	public void setCity(String city) {
		this.city = city;
	}
	public String getState() {
		return state;
	}
	public void setState(String state) {
		this.state = state;
	}
	public String getZip() {
		return zip;
	}
	public void setZip(String zip) {
		this.zip = zip;
	}
	public String getCountry() {
		return country;
	}
	public void setCountry(String country) {
		this.country = country;
	}
	
	
}
