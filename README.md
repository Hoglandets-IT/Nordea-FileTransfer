# Nordea File Transfer
File transfer specifications and examples for Nordea interfaces (Secure Envelope). The specifications for transferring already created files to Nordea.

## Links
- Secure Envelope - ApplicationRequest https://www.nordea.fi/Images/146-88693/ApplicationRequest.zip
- Secure Envelope - ApplicationResponse https://www.nordea.fi/Images/146-88696/ApplicationResponse.zip
- Test Certificate https://www.nordea.com/en/doc/certificateproductiondemo.zip
- Test Tool Secure Envelope https://girolink.plusgirot.se/jnlp/glwsjl43.jnlp
- Test Tool User Guide https://www.nordea.com/en/doc/corporate-access-test-tool-user-guide.pdf
- Nordea File Transfer (Ruby) https://github.com/mitigate-dev/nordea-filetransfer
- Nordea File Transfer (PHP) https://github.com/outl1ne/Nordea-WebService 

## Overview
### Source Files
Source files are base64-encoded and placed in the body of the ApplicationRequest message. The format of these files is not within the scope of this repository.

### Secure Envelope (ApplicationRequest)
The SecureEnvelope specification for sending files to Nordea consist of data in the ApplicationRequest format. The ApplicationRequest is a SOAP message with the following structure:

[Resources/ApplicationRequest.xml](ApplicationRequest.xml)

### Secure Envelope (ApplicationResponse)
The SecureEnvelope specification for receiving files from Nordea consist of data in the ApplicationResponse format. The ApplicationResponse is a SOAP message with the following structure:
[Resources/ApplicationResponse.xml](ApplicationResponse.xml)

### Signatures
[Resources/TestCertificate.p12](TestCertificate.p12) is a test certificate for signing and verifying the Secure Envelope messages. The password for the certificate is `WSNDEA1234`.

### Web Service Protocol information
[Resources/CorporateFileService.wsdl](CorporateFileService.wsdl)

### File Transfer
http://www.nordea.fi/sitemod/upload/Root/fi_org/liite/e/yritys/pdf/erasiir.pdf
http://www.nordea.fi/Corporate+customers/Payments+and+cards/Advice+on+payments+and+cards/Instructions/1433022.html
http://www.nordea.fi/Corporate+customers/Payments+and+cards/Advice+on+payments+and+cards/Example+files/1466002.html
https://filetransfer.nordea.com/services/CorporateFileService?wsdl

## Web Requests
### Basics
- SenderId: Nordea Customer Number
- RequestId: Unique ID for the request
- Timestamp: Timestamp of the request
- Language: Language of the request
- UserAgent: User agent of the request
- ReceiverId: 
### getUserInfo
Method: POST
URL: https://filetransfer.nordea.com:2020/services/CorporateFileService
```xml
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">
    <Body>
        <getUserInfoin xmlns="http://bxd.fi/CorporateFileService">
            <RequestHeader xmlns="http://model.bxd.fi">
                <SenderId>[string]</SenderId>
                <RequestId>[string]</RequestId>
                <Timestamp>[dateTime]</Timestamp>
                <Language>[string]</Language>
                <UserAgent>[string]</UserAgent>
                <ReceiverId>[string]</ReceiverId>
            </RequestHeader>
            <ApplicationRequest xmlns="http://model.bxd.fi">[base64Binary]</ApplicationRequest>
        </getUserInfoin>
    </Body>
</Envelope>
```
### uploadFile
### downloadFileList
### downloadFile
### deleteFile
