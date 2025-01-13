# Cloud-Computing-Cloud-Based-Face-Recognition-A-Serverless-Video-Processing-Application
The project involves developing a PaaS-based cloud application using AWS Lambda to enable face recognition for video streams, focusing on video splitting.
Set Up the Input Bucket

Create an AWS S3 bucket named <ASU ID>-input.
Configure the bucket to store .mp4 video files uploaded by clients (e.g., a workload generator).
Ensure the bucket triggers the Lambda function named video-splitting upon new video uploads.
Trigger the Video-Splitting Lambda Function

Configure the video-splitting Lambda function to activate whenever a new video is uploaded to the input bucket.
Use the ffmpeg library within the Lambda function to process videos.
Split the video into frames (Group-of-Pictures or GoP)

Store the output frames in folders named after the original video file (without extensions) in a second bucket.
Set Up the Stage-1 Bucket

Create an AWS S3 bucket named <ASU ID>-stage-1.
Store the output of the Lambda function here:
Each folder in the bucket corresponds to a video file and contains frames named output_00.jpg, output_01.jpg, ..., up to output_09.jpg.
Testing and Validation

IAM Role Setup:
Create an IAM user with permissions: s3:Get*, s3:PutObject, s3:List*, lambda:GetFunction, and cloudwatch:GetMetricData.
Workload Testing:
Use a workload generator to upload 100 video files to the input bucket.
Validate that:
All 100 videos trigger the Lambda function.
The stage-1 bucket contains 100 folders named after the input videos.
Each folder contains 10 correctly named .jpg images.
Performance Metrics

Measure and validate:
Lambda execution time (average ≤ 10 ms).
Concurrency level (≥ 5 concurrent executions).
