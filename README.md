# JPascalCoin

JPascalCoin is a Java library for PascalCoin. Currently only the JSON-RPC API is supported.
It's intended to be used both on Android or Java (java 1.7 is requiered).
Uses both google gson library for json deserialization and retrofit for rest calls. 
For logging uses java.util.logging, as it works by default on both Android and pure Java.
Junit tests are included

## Usage

Project has been uploaded to Maven central Repository
###Maven    
```
<dependency>   
	<groupId>com.github.davidbolet.jpascalcoin</groupId>    
	<artifactId>jPascalcoin</artifactId>      
	<version>1.0.2</version>  
</dependency>  
```

###Gradle
```
implementation 'com.github.davidbolet.jpascalcoin:jPascalcoin:1.0.2'   
```

Check junit test for full examples
You will need to include your account numbers and public keys (default key exported by wallet id b58PubKey)    


## Example:  Listing Wallet Accounts

```java
PascalCoinClient client =  new PascalCoinClientImpl("127.0.0.1",PascalCoinConstants.DEFAULT_MAINNET_RPC_PORT);
//use either <Encoded Public Key>, <B58 Public Key>
List<Account> accounts = client.getWalletAccounts("<Encoded Public Key>", "<B58 Public Key>", 0, 100);
```
## Full Example show Account's balance:
```java 
import java.io.IOException;
import com.github.davidbolet.jpascalcoin.api.client.*;
import com.github.davidbolet.jpascalcoin.api.model.Account;

public final class Example1
{
    public static void main(final String... args)
        throws IOException
    {
        PascalCoinClient client = new PascalCoinClientImpl();
        Account account = client.getAccount(0);
        System.out.println(String.format("Account's balance: %.4f PASC"+account.getBalance()));
    }
}
```

## Example: Sending funds

Unlocking wallet and sending funds

```java 
PascalCoinClient client =  new PascalCoinClientImpl("127.0.0.1",PascalCoinConstants.DEFAULT_MAINNET_RPC_PORT);
client.unlock("wallet_password");
Operation op = client.sendTo(accountSender, accountTarget, amount, fee, payload.getBytes(), PayLoadEncryptionMethod.AES, "password_to_encrypt_payload"); 
```

# Credits
Donations apreciated :)

PascalCoin -> Account 381309-50 (you can test sendTo function, if you want :)))

BitCoin -> 
![18zU5odGJqefdwzNmnj9teSJRZS5auEPRg](./bitcoin.png?raw=true "18zU5odGJqefdwzNmnj9teSJRZS5auEPRg")


David Bolet <davidbolet@gmail.com>
