# --------------------------------------------------------------------------
# Access Mechanism 
# --------------------------------------------------------------------------

The Dell PowerConnect switch module uses Network Device functionality of Puppet to interact with the PowerConnect switch.

# --------------------------------------------------------------------------
#  Supported Functionality
# --------------------------------------------------------------------------

	- Apply Firmware Update on the Switch


# -------------------------------------------------------------------------
# Functionality Description
# -------------------------------------------------------------------------


  1. Apply Firmware Update on the Switch
  		This will update the firmware of the switch with a new image.

    

# -------------------------------------------------------------------------
# Summary of parameters.
# -------------------------------------------------------------------------

	name: (Required)This parameter defines a dummy image name.
	 
	imageurl: This parameter defines the TFTP URL of the firmware image.
	          The value must be in the format tftp://${TFTPServerIPAddress}/${imageLocation}
	          The image name must have the firmware version appended to it eg. PC7000_M6348v5.1.2.3.stk
	
	forceupdate: This parameter determines whether firmware updates can be forcefully applied on the switch.
	             The possible values are true and false. The default value is false.
	             If the value is true, then the firmware image will be applied even if it's the same version as existing firmware version.
    
    
# -------------------------------------------------------------------------
# Parameter signature 
# -------------------------------------------------------------------------

	node "$switch_fqdn" {

    	powerconnect_firmware{

		    '$firmware-image':
		     imageurl       => '$firmware-imageurl',
		     forceupdate    => '$firmware-force',

   		 } 
   		 
	}
	

# --------------------------------------------------------------------------
# Usage
# --------------------------------------------------------------------------
   Refer to the examples in the manifest directory.
   The following file capture the details for the sample init.pp and supported files:

    - firmware_upgrade.pp
	
   Sample init.pp file:
   
   powerconnect_firmware {
       'image1':
	   imageurl       => tftp://10.10.10.10/PC7000_M6348v5.1.2.3.stk,
	   forceupdate    => true,
   }
		

   A user can create an init.pp file based on the above sample files and call the "puppet device" command , for example: 
   # puppet device

#-------------------------------------------------------------------------------------------------------------------------
# End
#-------------------------------------------------------------------------------------------------------------------------	