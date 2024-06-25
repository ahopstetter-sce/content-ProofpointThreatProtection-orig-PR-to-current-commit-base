# ProofpointThreatProtection - XSOAR Integration

## Introduction 
Repository to house the "pre-contribution" code work associated with the ProofpointThreatProtection intergration code that will be contributed to XSOAR for their Marketplace and continued support.

## Noteworthy items
1.	Originally coded/contributed by Randy Baldwin.
2.	Code tests can be conducted using the XSOAR standard pytest / pytest-mock tools.
3.  A built-in FastAPI server was coded into the testing process and runs *optionally* with the tests if the fastapi python module is accessible. This was put in place to facilitate testing of the client integration code while in a development environment where the assocaited API server resources were not accessible/usable for QA testing purposes. The FastAPI test server simply mimics all of the server responses the real API server would yield, allowing the client side to be fully tested without the need to have the server side present.
4.  If the fastapi module is not present the test code performs the more traditional "mock" style testing as completely enough to pass the demisto-sdk 70% minimum code coverage requirements. ( But it is still just mocked :) )
5.  If utilized, the FastAPI server binds itself to TCP port 8000 on the loopback address during testing. To alter these settings you can alter the 2 associated constants at the top of ProofpointThreatProtection_test.py.

## To obtain fastapi
```
python3 -m pip install fastapi
```

## Testing the code
1.  Code is fully test-able via the built in standard demisto-sdk pre-commit process and occurs automatically within that process. Note this test is the fully mocked version as the fastapi python module is not present within xsoar docker containers.
2.  To run tests locally / manually [includes fastapi server] from a linux/WSL bourne like shell ...
```
cd Packs/ProofpointThreatProtection/Integrations/ProofpointThreatProtection/
pytest
```
