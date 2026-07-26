## NOTE : THE BELOW GIVEN IS JUST A MIND DUMP OF I PICTURE THE APP TO MAYBE WORK , ITS NOT A STRICT CONCERETE FLOW TO FOLLOW , IMPROVEMENTS AND POLISHING IS NEEDED . THIS IS JUST A SNIPPET 


1. Both clients ( Ashton and naitik install chainguard on their pc : EG git clone <url>)
2. I run the app to use it : chainguard  ( cli apps starts running  ) and so does naitik  ( locally on different machines )
3. Then i want to send secrets.env file so i first establish connection with naitik thru his public key 
  i. cg ( Chainguard) -connect .public-key-naitik --receiver-name naitik  --sender-name Ashton  ( Request sent to establish connection with naitik ! Waiting for    response.)
  ii. Naitik sees the incoming request ( Incoming connection request from Ashton , press enter to accept , x to reject , q to exit the app )
  iii. Naitik presses enter ( Connection successfull , now you can chat , send files secretly here encrypted E2E ( whatever idk ))
4. Now I want to send the secrets.env file 
  i. cg -transfer --name secrets.env ./secrets.env -m "Here are the databaseCredentials " 
  ii. Naitik sees ( Ashton wants to send secrets.env accept | reject | send message back )
  