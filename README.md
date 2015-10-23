# pangya-server
Welcome to pangya-server an emulation server for Pangya FreshUp.

# pangya Crypt library
In the project files, you'll see references to a library "pang.dll"

"pang.dll" is a library used in some of my projects and will not be shared in this project. It will not be shared with the source code but maybe someone will can create it for you. Or maybe you'll create it for yourself.

To make it work with your project, "pangya.dll" must share some functions the server will be able to unnderstand.
  - _pangya_client_decrypt
  - _pangya_server_encrypt
  - _pangya_client_encrypt
  - _deserialize

defined as:

    #define DLLEXPORT EXTERN_C __declspec(dllexport)
    
    struct ret_struct {
	    int size;
	    char *data;
    };

    DLLEXPORT ret_struct pangya_client_decrypt(char *data, int size, char key);
    DLLEXPORT ret_struct pangya_server_encrypt(char *data, int size, char key);
    DLLEXPORT ret_struct pangya_client_encrypt(char *data, int size, char key, char packetid);
    DLLEXPORT UInt32 deserialize(UInt32 deserialize);

"pangya_client_decrypt" must accept the full packet send by the client as data and must return the decrypted packet starting with the Id of the packet.

"pangya_server_encrypt" must accept the decrypted packet as data starting with the Id of the packet.

"pangya_client_encrypt" must accept the decrypted packet as data starting with the Id of the packet.

If you need more details about dll format, you still can send an e-mail to bugreport@shadosoft-tm.com
