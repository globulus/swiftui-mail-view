# SwiftUIMailView

The `MailView` allows you to **send mail from SwiftUI**. You can:

* Determine if you can send mail or not.
* Pass subject, message and recipients to the view via a binding.
* Attach files to the email.
* Receive success or failure result after sending the email.

The end result looks like this:

![in action](https://swiftuirecipes.com/user/pages/01.blog/send-mail-in-swiftui/ezgif-3-c21e985ad818.gif)

### Recipe

Check out [this recipe](https://swiftuirecipes.com/blog/send-mail-in-swiftui) for in-depth description of the component and its code. Check out [SwiftUIRecipes.com](https://swiftuirecipes.com) for more **SwiftUI recipes**!

### Sample usage

```swift
struct MailViewTest: View {
   @State private var mailData = ComposeMailData(subject: "A subject",
                                                 recipients: ["i.love@swiftuirecipes.com"],
                                                 message: "Here's a message",
                                                 attachments: [AttachmentData(data: "Some text".data(using: .utf8)!,
                                                                              mimeType: "text/plain",
                                                                              fileName: "text.txt")
                                                 ])
   @State private var showMailView = false

    var body: some View {
        Button(action: {
            showMailView.toggle()
        }) {
            Text("Send mail")
        }
        .disabled(!MailView.canSendMail)
        .sheet(isPresented: $showMailView) {
            MailView(data: $mailData) { result in
                print(result)
            }
        }
    }
}
```

### Installation

This component is distrubuted as a **Swift package**. 
