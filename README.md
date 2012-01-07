hideyukisaito/ofxOsc
====================
based on the ofxOsc included in of_preRelease_v007_osx
  
changes:  
ofxOscReceiver dispatches ofEvent "onMessageReceived" with ofxOscMessage as ofEventArgs on received new message.  
So we can get ofxOscMessage without using receiver.hasWaitingMessages\(\).  
  
i.e.
  
```
void testApp::setup()
{
    receiver.setup(10000);
    ofAddListener(receiver.onMessageReceived, this, &testApp::onMessageReceived);
}

void testApp::onMessageReceived(ofxOscMessage &msg)
{
    string addr = msg.getAddress();
    string message = msg.getArgAsString();
}
```
