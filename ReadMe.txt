��ôʹ�ã�

һ   �����
	   1 �ƶ�Ҫ�����Ľӿ�,������Ľӿڴ���ṩ���ͻ��ˣ���:
	      interface TestServiceItf {
	         void add(int a,int b);
	        }
	   2 �ṩһ�������ʵ��
	   
	   3 ����һ��RPCService����RPCService app = new RPCService(1082);
	   
	   4 ������ķ���app.exportService("test", new TestService());
	   
	   5 ����RPCService.run()
   
   �μ�:
  com.lesen.rpc.example.ServiceTest
  
    package com.lesen.rpc.example;
	import com.lesen.rpc.common.export.TestService;
	import com.lesen.rpc.service.RPCService;
	
	public class ServiceTest {
	
		public static void main(String[] args) throws Exception {
			RPCService app = new RPCService(1082);
			app.exportService("test", new TestService());
			app.run();
		}
	}
�� �ͻ���
   com.lesen.rpc.example.ClientTest
   
        package com.lesen.rpc.example;
		import com.lesen.rpc.client.RPCClient;
		import com.lesen.rpc.common.export.Service;
		
		public class ClientTest {
		
			public static void main(String[] args) {
				String serverName = "test";
				String rpcUri = "rpc://127.0.0.1:1082";
				RPCClient client = new RPCClient(rpcUri);
				client.registDecodeEncode(new PersonDecodeEncode());
				client.connectService();
				
				Service service = client.getRemoteService(serverName, Service.class);
				System.out.println(service.test("12"));
				client.close();
			}
		}
         