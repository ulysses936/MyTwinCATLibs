# MyTwinCATLibs
我写的一些程序，希望大家能指导

## TcpConnection
```pascal
IF TcpConnection.Connect('192.168.88.136', 60002) THEN
  //CheckConnectionStatue, if connection failed, retuen TRUE
	ConnectionStatus := TcpConnection.CheckState();

  //Receive once
	IF bReceive THEN
		recvBytes := TcpConnection.Receive(ADR(dataToRecv), SIZEOF(dataToRecv));
		bReceive := (recvBytes = 0);
	END_IF

  //Receive cyclically
	recvBytes := TcpConnection.Receive(ADR(dataToRecv), SIZEOF(dataToRecv));

  //If connection failed, close currect connection and the connection method will reconnection automatically
	IF ConnectionStatus THEN
		TcpConnection.Close();
	END_IF

  //Send once
	IF SEND THEN
		SEND := NOT TcpConnection.Send(ADR(dataToSend),SIZEOF(dataToSend));
	END_IF

  //Send cyclically
	IF SEND2 THEN
		TcpConnection.Send(ADR(dataToSend),SIZEOF(dataToSend));
	END_IF
END_IF
```
