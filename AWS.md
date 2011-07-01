# IAM

Basic policy for allowing one bucket

    {
      "Statement": [
        {
          "Action": "s3:*",
          "Effect": "Allow",
          "Resource": ["arn:aws:s3:::MY_BUCKET", "arn:aws:s3:::MY_BUCKET/*"]
        }
      ]
    }
    
Replace MY_BUCKET with your bucket name