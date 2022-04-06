https://docs.microsoft.com/en-us/dotnet/orleans/overview


https://docs.microsoft.com/zh-cn/azure/active-directory/identity-protection/overview-identity-protection

```csharp
ISiloHostBuilder ISiloHostBuilder.UseLocalhostClustering(
    int siloPort = 11111, 
    int gatewayPort = 30000, 
    IPEndPoint primarySiloEndpoint = null, 
    string serviceId = "dev", 
    string clusterId = "dev")
```


```
dotnet add app/app.csproj reference lib/lib.csproj

(base) whao@Williams-MacBook-Pro hello_world % dotnet sln add ./Client/Client.csproj 
Project `Client/Client.csproj` added to the solution.
(base) whao@Williams-MacBook-Pro hello_world % dotnet sln add ./GrainInterfaces/GrainInterfaces.csproj
Project `GrainInterfaces/GrainInterfaces.csproj` added to the solution.
(base) whao@Williams-MacBook-Pro hello_world % dotnet sln add ./Grains/Grains.csproj                  
Project `Grains/Grains.csproj` added to the solution.
(base) whao@Williams-MacBook-Pro hello_world % dotnet add Grains/Grains.csproj reference GrainInterfaces/GrainInterfaces.csproj
Reference `..\GrainInterfaces\GrainInterfaces.csproj` added to the project.
(base) whao@Williams-MacBook-Pro hello_world % dotnet add Silo/Silo.csproj reference GrainInterfaces/GrainInterfaces.csproj
Reference `..\GrainInterfaces\GrainInterfaces.csproj` added to the project.
(base) whao@Williams-MacBook-Pro hello_world % dotnet add Silo/Silo.csproj reference Grains/Grains.csproj                  
Reference `..\Grains\Grains.csproj` added to the project.
(base) whao@Williams-MacBook-Pro hello_world % dotnet add Client/Client.csproj reference GrainInterfaces/GrainInterfaces.csproj
Reference `..\GrainInterfaces\GrainInterfaces.csproj` added to the project.

```

Output
```
(base) whao@Williams-MacBook-Pro Client % dotnet run
info: Orleans.OutsideRuntimeClient[100313]
      ---------- Initializing OutsideRuntimeClient on Williams-MacBook-Pro.local at 192.168.31.75 Client Id = *cli/8d5ad8a4 ----------
info: Orleans.OutsideRuntimeClient[100314]
      ---------- Starting OutsideRuntimeClient with runtime Version='3.6.1+3b9db14d44c701e4c34635af4bd1be28a02aa4da (Release).' in AppDomain=<AppDomain.Id=1, AppDomain.FriendlyName=Client>
info: Orleans.Messaging.GatewayManager[101309]
      Found 1 gateways: [gwy.tcp://127.0.0.1:30000/0]
info: Orleans.Networking[0]
      Establishing connection to endpoint S127.0.0.1:30000:0
info: Orleans.Networking[0]
      Connected to endpoint S127.0.0.1:30000:0
info: Orleans.Networking[0]
      Connection [Local: 127.0.0.1:65244, Remote: 127.0.0.1:30000, ConnectionId: 0HMGNQI6JJI4J] established with S127.0.0.1:30000:0
info: Orleans.OutsideRuntimeClient[100929]
      ---------- Started OutsideRuntimeClient with Global Client ID: C192.168.31.75:0:-386949089*cli/8d5ad8a4@fd9368b1, client GUID ID: *cli/8d5ad8a4
info: Orleans.ClientOptionsLogger[0]
      Configuration Orleans.Configuration.ClientMessagingOptions: 
      ClientSenderBuckets: 8192
      PreferredFamily: InterNetwork
      NetworkInterfaceName: 
      LocalAddress: 
      ResponseTimeout: 00:00:30
      ResponseTimeoutWithDebugger: 00:30:00
      DropExpiredMessages: True
      BufferPoolBufferSize: 4096
      BufferPoolMaxSize: 10000
      BufferPoolPreallocationSize: 250
      PropagateActivityId: False
      LargeMessageWarningThreshold: 85000
      MaxMessageHeaderSize: 10485760
      MaxMessageBodySize: 104857600
      
info: Orleans.ClientOptionsLogger[0]
      Configuration Orleans.Configuration.ClusterOptions: 
      ClusterId: dev
      ServiceId: OrleansBasics
      
info: Orleans.ClientOptionsLogger[0]
      Configuration Orleans.Configuration.ConnectionOptions: 
      ProtocolVersion: Version1
      ConnectionsPerEndpoint: 1
      ConnectionRetryDelay: 00:00:01
      OpenConnectionTimeout: 00:00:05
      
info: Orleans.ClientOptionsLogger[0]
      Configuration Orleans.Configuration.StaticGatewayListProviderOptions: 
      Gateways.0: gwy.tcp://127.0.0.1:30000/0
      
info: Orleans.ClientOptionsLogger[0]
      Configuration Orleans.Configuration.StatisticsOptions: 
      PerfCountersWriteInterval: 00:00:30
      LogWriteInterval: 00:05:00
      CollectionLevel: Info
      
Client successfully connected to silo host 




 Client said: 'Good morning, HelloGrain!', so HelloGrain says: Hello!


info: Orleans.Messaging.GatewayManager[101309]
      Refreshed the live gateway list. Found 1 gateways from gateway list provider: [S127.0.0.1:30000:0]. Picked only known live out of them. Now has 1 live gateways: [S127.0.0.1:30000:0]. Previous refresh time was = 04/06/2022 13:51:29
info: Orleans.Messaging.GatewayManager[101309]
      Refreshed the live gateway list. Found 1 gateways from gateway list provider: [S127.0.0.1:30000:0]. Picked only known live out of them. Now has 1 live gateways: [S127.0.0.1:30000:0]. Previous refresh time was = 04/06/2022 13:52:29

info: Orleans.Messaging.GatewayManager[101309]
      Refreshed the live gateway list. Found 1 gateways from gateway list provider: [S127.0.0.1:30000:0]. Picked only known live out of them. Now has 1 live gateways: [S127.0.0.1:30000:0]. Previous refresh time was = 04/06/2022 13:51:29
info: Orleans.Messaging.GatewayManager[101309]
      Refreshed the live gateway list. Found 1 gateways from gateway list provider: [S127.0.0.1:30000:0]. Picked only known live out of them. Now has 1 live gateways: [S127.0.0.1:30000:0]. Previous refresh time was = 04/06/2022 13:52:29
info: Orleans.Messaging.GatewayManager[101309]
      Refreshed the live gateway list. Found 1 gateways from gateway list provider: [S127.0.0.1:30000:0]. Picked only known live out of them. Now has 1 live gateways: [S127.0.0.1:30000:0]. Previous refresh time was = 04/06/2022 13:53:29
```