Spin up EC2 instance with Public Amazon Linux AMI, defined [here](https://docs.aws.amazon.com/lambda/latest/dg/current-supported-versions.html)

Instructions:
```Shell
	virtualenv -p python27 env
	source env/bin/activate
	
	# Install OS and Python libraries/packages
	pip install mxnet
	sudo yum install libgomp

	# Copy files out of virtualenv
	cp -r env/lib/python2.7/site-packages/* .
	cp -r env/lib64/python2.7/site-packages/* .

	# Zip up deployment package
	zip -r -9 ../lambda.zip ./* -x "*.pyc" "env/*" "notebooks/*" "boto*" "wheel*" "setup*" "pip*" 
	
	# Uplaod deployment package
	aws s3 cp ../lambda.zip s3://jakechenawstemp/
	
```
