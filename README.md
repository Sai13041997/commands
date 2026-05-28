# commands


1. leaf to intermediate: 

 -> Checking CA issuer of leaf:

  openssl x509 -in MVS_OLV_TEST_2026.cer -noout -text | grep -A1 "CA Issuers"

  -> Output: 

  CA Issuers - URI:http://certificates.godaddy.com/repository/gdig2.crt
            X509v3 Authority Key Identifier: 

 -> Getting Intermeadiate:

  curl -o gdig2.crt http://certificates.godaddy.com/repository/gdig2.crt

2. Intermediate to root:

  -> Checking CA issuer of intermediate:

   $ openssl x509 -in gdig2.crt -noout -text | grep -A1 "CA Issuers"
                           or
    openssl x509 -in gdig2.crt -noout -text
   
 -> Output:

  CA Issuers - URI:https://certs.godaddy.com/repository/gdroot-g2.cr
            X509v3 Authority Key Identifier: 


  -> Getting root

   $ curl -o gdroot-g2.cer https://certs.godaddy.com/repository/gdroot-g2.crt

3. Verify CA Bundle: 
  
  $ openssl verify -CAfile gdroot-g2.cer -untrusted gdig2.crt MVS_OLV_TEST_2026.cer
   
 -> Output: 
   
    MVS_OLV_TEST_2026.cer=ok

4. Checking certificate type
  
   head gdroot-g2.cer
   
   head gdig2.crt 
   
   head MVS_OLV_TEST_2026.cer


5. Converting to .pem if they are not in .pem 

  $ openssl x509 -in gdig2.crt -out gdig2.pem -outform PEM
  
  $ openssl x509 -in MVS_OLV_TEST_2026.crt -out MVS_OLV_TEST_2026.pem -outform PEM

  Root is already pem so I didn't convert.

6. Convert it into bundle: 
  
  $ cat  gdig2.pem gdroot-g2.crt > truststore.pem
