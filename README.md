### Product Description: Claude-Wisdom-AI

Claude-Wisdom-AI is an advanced chatbot framework that leverages the power of Anthropic's Claude LLM, one of the foundational models provided by Amazon Bedrock. This repository offers a robust and customizable chatbot solution designed for seamless deployment on AWS, supporting both text and image-based conversations. The chatbot can be tailored with personalized instructions and external knowledge sources, making it ideal for businesses looking to deploy intelligent, context-aware conversational agents. With built-in governance features, Claude-Wisdom-AI ensures secure and controlled access, making it suitable for enterprise-level applications.

Key Features:
- **Text and Image Conversations:** Engage users with both text and image responses using Claude 3's capabilities.
- **Bot Personalization:** Customize your chatbot with specific instructions and external knowledge, and publish it as a stand-alone API.
- **Administrator Dashboard:** Monitor usage and performance through a comprehensive admin interface.
- **LLM-powered Agent:** Automate complex tasks by integrating external tools and breaking down tasks into manageable steps.
- **Multi-language Support:** Available in multiple languages including English, Japanese, Korean, Chinese, French, German, Spanish, and Italian.
- **Super-easy Deployment:** Deploy the entire solution with minimal effort using AWS CloudShell or CDK, ensuring scalability, reliability, and security.

### Step-by-Step Deployment Guide: Claude-Wisdom-AI

#### Prerequisites:
- Ensure you have access to the [Amazon Bedrock](https://aws.amazon.com/bedrock/) service in the desired AWS region (e.g., us-east-1).
- Open the [Bedrock Model Access](https://us-east-1.console.aws.amazon.com/bedrock/home?region=us-east-1#/modelaccess) page and enable the required models (`Anthropic / Claude 3 Haiku`, `Anthropic / Claude 3 Sonnet`, etc.).

#### Deployment via AWS CloudShell

1. **Clone the Repository:**
   - Open [AWS CloudShell](https://console.aws.amazon.com/cloudshell/home) in your desired region.
   - Execute the following commands to clone the repository and set up the environment:
     ```bash
     git clone https://github.com/awsstudygroup/Claude-Wisdom-AI.git
     cd Claude-Wisdom-AI
     chmod +x bin.sh
     ```

2. **Run the Deployment Script:**
   - Execute the deployment script:
     ```bash
     ./bin.sh
     ```
   - You will be prompted to specify if you are a new user or continuing from a previous version. If you are not upgrading from version 0.x, enter `y`.

3. **Optional Parameters:**
   - You can enhance security and customize deployment by adding optional parameters such as disabling self-registration, restricting IP ranges, or specifying email domains.
   - Example command with optional parameters:
     ```bash
     ./bin.sh --disable-self-register --ipv4-ranges "192.0.2.0/25,192.0.2.128/25" --allowed-signup-email-domains "example.com" --bedrock-region "us-west-2"
     ```

4. **Access the Application:**
   - After approximately 35 minutes, the script will output the URL of the deployed application.
   - Visit the `Frontend URL` from your browser to access the chatbot interface.

#### Deployment via AWS CDK

1. **Install Required Tools:**
   - Ensure you have UNIX, Docker, and Node.js installed, or use [Cloud9](https://github.com/aws-samples/cloud9-setup-for-prototyping).
   - Clone the repository:
     ```bash
     git clone https://github.com/awsstudygroup/Claude-Wisdom-AI.git
     cd Claude-Wisdom-AI/cdk
     npm ci
     ```
   - Install the AWS CDK:
     ```bash
     npm i -g aws-cdk
     ```

2. **Bootstrap and Deploy:**
   - Bootstrap the environment for the region you are deploying to:
     ```bash
     cdk bootstrap aws://<account-id>/us-east-1
     ```
   - Deploy the project using CDK:
     ```bash
     cdk deploy --require-approval never --all
     ```

3. **Access the Application:**
   - Once the deployment completes, access the `FrontendURL` output from the CDK deployment to start using the chatbot.

#### Post-Deployment Configuration

1. **Set Up Bot Personalization:**
   - Configure personalized instructions and external knowledge sources as per the documentation.
   
2. **Monitor and Manage:**
   - Use the administrator dashboard to monitor usage and manage the chatbot.

3. **Additional Configuration:**
   - Review the optional settings in `cdk.json` to further customize the deployment, including IP restrictions, NAT gateway counts, and self-sign-up options.

4. **Clean-Up:**
   - If you need to remove the resources, use `cdk destroy` or manually delete the CloudFormation stacks.

For more details on advanced configurations, such as integrating external identity providers or customizing the chatbot's behavior, refer to the repository's documentation.
