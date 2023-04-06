# My-first-blockchain
overview
public class Block {
  private int index;
  private long timestamp;
  private String hash;
  private String previousHash;
  private String data;

  // Constructor
  public Block(int index, long timestamp, String data, String previousHash) {
    this.index = index;
    this.timestamp = timestamp;
    this.data = data;
    this.previousHash = previousHash;
    this.hash = calculateHash();
  }

  // Getters and setters

  public int getIndex() {
    return index;
  }

  public void setIndex(int index) {
    this.index = index;
  }

  public long getTimestamp() {
    return timestamp;
  }

  public void setTimestamp(long timestamp) {
    this.timestamp = timestamp;
  }

  public String getHash() {
    return hash;
  }

  public void setHash(String hash) {
    this.hash = hash;
  }

  public String getPreviousHash() {
    return previousHash;
  }

  public void setPreviousHash(String previousHash) {
    this.previousHash = previousHash;
  }

  public String getData() {
    return data;
  }

  public void setData(String data) {
    this.data = data;
  }

  // Calculate the hash for the current block
  public String calculateHash() {
    String dataToHash = previousHash + Long.toString(timestamp) + data;
    MessageDigest digest;
    String hash = null;
    try {
      digest = MessageDigest.getInstance("SHA-256");
      byte[] bytes = digest.digest(dataToHash.getBytes(StandardCharsets.UTF_8));
      hash = DatatypeConverter.printHexBinary(bytes);
    } catch (NoSuchAlgorithmException ex) {
      ex.printStackTrace();
    }
    return hash;
  }
}
