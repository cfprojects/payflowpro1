If you use the CFX_PayFlowPro tag to connect to PayPal's PayFlowPro service (formerly owned by Verisign) you should be aware that it will stop working in September of 2009.  You must transition to one of their newer connection methods before then.

Here is a drop in replacement custom tag you can use.  You should be able to pretty much just change your code from "CFX_PayFlowPro" to "CF_PayFlowPro".  If you run into any issues and end up modifying the tag, please let me know and I'll get the changes worked back into the original.

Ryan Stille
ryan@cfwebtools.com
http://www.stillnetstudios.com

Usage examples:


Simple CC charge:
<CF_PAYFLOWPRO QUERY   = "RESULT"
            HOSTADDRESS   	= "#cfg_pfp_host#"
            HOSTPORT       	= "443"
            TIMEOUT        	= "30"
            PROXYPASSWORD  	= ""
            TRXTYPE        	= "S"
            TENDER         	= "C"
            PARTNER 		= "PayPal"
            VENDOR 		= ""
            USER    		= "your_username"  
            PWD            	= "your_password"
            ACCT           	= "#cardnum#"
            EXPDATE        	= "#Form.ccexpmo##Form.ccexpyr#"
	    CVV2		= "#Form.cvv2#"
            AMT            	= "#amt#"
            COMMENT1       	= "#Form.email#"
            COMMENT2       	= "Purchased qty #Form.qty# of #Form.product#"
            EMAIL		= "#Form.email#"
            NAME		= "#Form.ccname#"
            STREET		= "#Form.ccaddress#"
            CITY		= "#Form.cccity#"
	    STATE		= "#Form.ccstate#"
	    ZIP			= "#Form.cczip#"
            >



Setup recurring billing profile:
	<CF_PAYFLOWPRO QUERY    = "RESULT"
                HOSTADDRESS   	= "#cfg_pfp_host#"
                HOSTPORT       	= "443"
                TIMEOUT        	= "30"
                TRXTYPE        	= "R"
                TENDER         	= "C"
                PARTNER 	= "PayPal"
            	VENDOR 		= ""
           	USER    	= "your_username"  
            	PWD            	= "your_password"
                ACCT           	= "#Arguments.ccnum#"
                EXPDATE        	= "#Arguments.ccexpmo##Arguments.ccexpyr#"
                AMT            	= "#lcfg_services[Arguments.subtype].cost#"
                COMMENT1       	= ""
		ACTION		= "A"
		EMAIL		= "#qryuser.email#"
		NAME		= "#Arguments.name#"
		STREET		= "#Arguments.address#"
		CITY		= "#Arguments.city#"
		STATE		= "#Arguments.state#"
		ZIP		= "#Arguments.zip#"
		START		= "#startChargeDate#"
		PROFILENAME	= "#qryuser.email#"
		PAYPERIOD	= "MONT"
		OPTIONALTRX	= "#optionaltrx#"
		OPTIONALTRXAMT	= "#optionaltrxamt#"
		TERM		= "0"
		>