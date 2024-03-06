# How to sync swiftdata with iCloud

If you want to sync your app's data to iCloud, go to the Signing & Capabilities settings for your app's target, then:

- Add the iCloud capability.
- Select CloudKit from its options.
- Press + to add a new CloudKit container, or select one of your existing ones.
- Add the Background Modes capability.
- Check the box "Remote Notifications" checkbox from its options.

…and that's it: your app is now configured to sync all its data with iCloud.

Tip: Although you can attempt to test iCloud support in the simulator, I've found it rarely works well – it's much better to test on a real device.

Although the configuration is complete, you might need to make some changes to your SwiftData models because CloudKit has a few very specific requirements. Annoyingly, if you don't follow these requirements your iCloud sync will silently fail, so here they are:

- You cannot use @Attribute(.unique) on any property you want to sync to CloudKit.
- All properties must either have default values or be marked as optional, alongside their initializer.
- All relationships must be marked optional. This is Particularly Annoying™, but it's a requirement so there's not much we can do.

## additional 
- if you see error saying "cannot modify" something, go iCloud dashboard, create a custom zone in Private database.

# source
https://www.hackingwithswift.com/quick-start/swiftdata/how-to-sync-swiftdata-with-icloud
