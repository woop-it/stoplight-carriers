# Upload a delivery document

The endpoint for adding a document uses the mulipart/form-data format which allows to send files in addition to the classical data in a form.

First of all, the **Content-Type** header must be sent like this: `multipart/form-data; boundary=<calculated>` the boundary is calculated by the browser or the Http library used.


Each part of the form is sent this way:

- For the files 

```json
Content-Disposition: form-data; name="{NAME}"; filename="{FILE NAME}"[CRLF].
Content-Type: {MIME TYPE}[CRLF][CRLF].
[CRLF]
{CONTENT}

```
- For classic data

```json
Content-Disposition: form-data; name="{NAME}"[CRLF].
[CRLF]
{VALUE}
```

The [CRLF] corresponds to a return to a line return "\r\n". NAME and FILE NAME must not contain a quotation mark (") or a line break (\r or \n).

Data are separated by the boundary.


### Usage

**Postman**

![document](../../assets/images/upload-document.png)

**Javascript**

Native from browsers: [form-data](https://developer.mozilla.org/fr/docs/Web/API/FormData/FormData)

**NodeJs**

With the library: [form-data](https://www.npmjs.com/package/form-data)

** Java (Android) **

With [Retrofit](https://futurestud.io/tutorials/retrofit-2-how-to-upload-files-to-server)

** Java (SpringBoot) **

With [HttpClient](https://www.baeldung.com/httpclient-post-http-request#post-multipart-request)

