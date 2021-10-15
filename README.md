### there are three variations of this app in the repository, 
## upload multiple files to google drive by creating a folder named using the username and email provided by user input
## upload multiple files to google drives by creating a folder named using the username and email provided by the database
## upload multiple files to google drives by creating a folder named using the username and email, and a file that contains log of file names plus a description provided by user input

i will explain each one and how to use it
#


## Script : Google Apps Script
~~~javascript
function doPost(e) {

}
~~~

### Flow :
- Retrieve data, filename and mimetype as ``e.parameters.data``, ``e.parameters.filename`` and ``e.parameters.mimetype``, respectively.
- Decode the data using ``Utilities.base64Decode()``.
- Create blob using ``Utilities.newBlob()``.
- Create the file in the root folder of Google Drive.

## Script : HTML
``https://script.google.com/macros/s/#####/exec`` is the URL obtained when the Web Apps was deployed. P

~~~html
<!DOCTYPE html>

</html>
~~~

### Flow :
- Using ``FileReader()``, retrieve base64 encoded file, filename and mimetype.
- Add input with type="hidden" to ``#form`` as text data.
    - ``replace(/^.*,/, '')`` is used for removing a header of encoded data.
    - ``match(/^.*(?=;)/)[0]`` is used for retrieving mimetype of uploading file.
- When a submit button is clicked, the base64 data is sent to ``doPost()`` of GAS.

## Note :
- In order to use this, after the script is modified, please redeploy Web Apps as a new version. By this, the latest script is reflected to Web Apps.
- This sample script can upload one file. If you want to upload several files, please modify script.  ``var file = this.files[0];`` means the selected first file. When there are some files, it is ``files[1], files[2] ....``.
