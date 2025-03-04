# User Defaults vs. Keychain

**User Defaults** is a property list (plist) that is a key-value store for data that persists across an app. It supports the following types: Strings, Numbers, Dates, Arrays, Dictionaries, Boolean, Data. However, User Defaults is deleted if the data from the app is deleted. Keychain data would persist across app deletions.

**Good For:** Simple User Preferences (theme)  
**Not Good For:** Private Data  

---

**Keychain** is different because all the data is encrypted (iOS Security Framework). It is an encrypted container that persists as long as the device data isn’t wiped.

**Good For:** Private/Sensitive Data, Subscription Status
**Not Good For:** Simple, frequently accessed data (due to performance)  

