# react-aws-s3
Open Source Module to Upload your Media and files into AWS S3 Bucket directly from Front-end React.

### https://www.npmjs.com/package/react-aws-s3
# S3Client AWS-S3

S3Client - A Javascript Library for AWS S3 File Upload

Using NPM

```
npm install --save react-aws-s3
```
Using Yarn 

```
yarn add react-aws-s3
```



# Examples Uploading An Image

## ***Uploading to S3***

```js
import S3 from 'react-aws-s3';

const config = {
    bucketName: 'myBucket',
    dirName: 'media', /* optional */
    region: 'eu-west-1',
    accessKeyId: 'JAJHAFJFHJDFJSDHFSDHFJKDSF',
    secretAccessKey: 'jhsdf99845fd98qwed42ebdyeqwd-3r98f373f=qwrq3rfr3rf',
    s3Url: 'https:/your-custom-s3-url.com/', /* optional */
}

const ReactS3Client = new S3(config);
/*  Notice that if you don't provide a dirName, the file will be automatically uploaded to the root of your bucket */

/* This is optional */
const newFileName = 'test-file';

ReactS3Client
    .uploadFile(file, newFileName)
    .then(data => console.log(data))
    .catch(err => console.error(err))

  /**
   * {
   *   Response: {
   *     bucket: "myBucket",
   *     key: "image/test-image.jpg",
   *     location: "https://myBucket.s3.amazonaws.com/media/test-file.jpg"
   *   }
   * }
   */
});
```

## ***Deleting an existing file in your bucket***

In this case the file that we want to delete is in the folder 'photos'

```js
import S3 from 'react-aws-s3';


const config = {
    bucketName: 'myBucket',
    dirName: 'media', /* optional */
    region: 'eu-west-1',
    accessKeyId: 'JAJHAFJFHJDFJSDHFSDHFJKDSF',
    secretAccessKey: 'jhsdf99845fd98qwed42ebdyeqwd-3r98f373f=qwrq3rfr3rf',
    s3Url: 'https:/your-custom-s3-url.com/', /* optional */
}

const ReactS3Client = new S3(config);

const filename = 'hello-world.docx';

/* If the file that you want to delete it's in your bucket's root folder, don't provide any dirName in the config object */

//In this case the file that we want to delete is in the folder 'photos' that we referred in the config object as the dirName

ReactS3Client
    .deleteFile(filename)
    .then(response => console.log(response))
    .catch(err => console.error(err))

  /**
   * {
   *   Response: {
   *      ok: true,
          status: 204,
          message: 'File deleted',
          fileName: 'hello-world.docx'
   *   }
   * }
   */
});
```

Defaults your bucket to `public-read` : http://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html

`config`
  * `bucketName` **required** - Your S3 bucket
  * `dirName` **required** - Your S3 folderName/dirName
  * `region` **required** - Your S3 bucket's region
  * `accessKeyId` **required** - Your S3 `AccessKeyId`
  * `secretAccessKey` **required** - Your S3 `SecretAccessKey`
  * `s3Url` **optional** - Your S3 URL

## License


## ***S3 Bucket Policy***

Doc: http://docs.aws.amazon.com/AmazonS3/latest/dev/example-bucket-policies.html


MIT
