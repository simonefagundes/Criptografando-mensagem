string mensagemSecreta = "Dados secretos";

byte[] textoCifrado = new byte[0];

byte[] chave = new byte[0];

byte [] vetorInicialização = new byte [];

using (Aes aes = Aes.Create())

{
    chave = aes.Key;
    vetorInicialização = aes.IV;
    
    iCryptoTransForm cryptoTransform = aes.CreateEncryptor();
    
    using (MemoryStream memoryStream = new MemoryStream())
    
    using (CryptoStream cryptoStream = new CryptoStream(memoryStream, cryptoTransform, CryptoStreamMode.Write))
        {
            using (StreamWriter streamWriter = new StreamWriter (cryptoStream))
            {
                streamWriter.Write("mensagemSecreta");

            }
           
            textoCifrado = memoryStream.toArray();
        }

}


Console.Writeline("Mensagem original: " {0}, mensagemSecreta);
ExibirBytes("Chave: ", chave);
ExibirBytes("Texto encriptado: ", textoCifrado);
    Console.ReadLine();

