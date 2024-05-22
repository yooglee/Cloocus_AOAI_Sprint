# GPT 기초, 사용 사례 및 샘플 솔루션 - 한국어 버전
이 리포지토리에는 Azure OpenAI에서 제공하는 GPT(Generative Pre-trained Transformer)를 사용하는 기본 방법을 이해하고 샘플 솔루션을 및 다양한 사용 사례를 통해 이해에 도움이 되는 리소스가 포함되어 있습니다. 해당 리포지토리는 아래를 참고하고 있으며 한국 환경에 맞게 최적화 되어 있습니다.
Original Repo: https://github.com/Azure/azure-openai-samples

## Update 정리
>**Python 버전은 3.11.4, Azure OpenAI 버전은 1.13.3에서 실행하도록 코드를 수정하였습니다. - 2024-03-17**  
>해당 컨텐츠는 DevContainer 기반으로 개발에 필요한 환경설정이 정의되어져 있습니다. GitHub Codespace를 활용하거나, 로컬에 Docker를 설치한 상태에서 Visual Stduio Code IDE에 해당 Repository를 다운로드 받을 경우, 자동으로 컨테이너에 개발환경(Python Runtime 3.11.4, Azure OpenAI 1.13.3)을 설치합니다. .env 파일에 필수 API 정보를 입력하고 저장후 사용하세요.  
----  
`나만의 Jarvis 비서` 만들기가 추가되었습니다. 외부 API를 말로 쉽게 호출하여 사용할 수 있습니다. [실습이동](./quick_start/11_my_jarvis_stt_chatgpt_tts.ipynb)  
![나만의 비서 만들기](./quick_start/assets/stt_chatgpt_tts.png)

## GPT란?
GPT(Generative Pre-trained Transformer)는 OpenAI에서 개발한 LLM(Large Language Model)입니다. 트랜스포머 아키텍처 기반의 딥러닝 모델입니다. 자세한 내용은 [OpenAI](https://openai.com)를 참조하세요.
간단하게 정리된 문서는 다음을 참고하세요.
- [Azure OpenAI 소개 - 한글 deck](http://azure.studydev.com/openai/aoai_2023_201.pdf)
- [Azure OpenAI 서비스 최신 업데이트 - 한글 deck](http://azure.studydev.com/openai/aoai_2024_q1.pdf)

## 리소스
다음의 순서로 GPT를 학습할 수 있습니다.

- [(누구나) Prompt Engineering - 기초](http://azure.studydev.com/openai/aoai_2024_pe_01.pdf)

- [(누구나) Prompt Engineering - Playground에서 놀기](http://azure.studydev.com/openai/aoai_2024_pe_02.pdf)

- [(개발자) Prompt Engineering - IDE에서 개발](http://azure.studydev.com/openai/aoai_2024_pe_03.pdf)

- [(개발자) Prompt Engineering - Quick Start](./quick_start/): GPT 사용을 빠르게 시작할 수 있는 노트북 모음입니다.

- [Use Cases | Kakao Navi 길찾기 API 통합](./use_cases/kakao_navi/notebooks/kakao_navi.ipynb): GPT의 Function Calling 기능에 실시간 카카오 Navi API를 연동하는 방법을 학습합니다.

----

## 실습 동영상
- [코드 기반으로 알아보는 프롬프트 엔지니어링 기초](https://youtu.be/XQ917ZOaaOk)
>Python 코드 기반으로 프롬프트 엔지니어링을 하는 방법을 소개합니다. 해당 영상은 Python Runtime 3.11.4, Azure OpenAI 1.13.3 버전의 환경에서 실행할 수 있도록 소스 코드(GitHub Repository)와 개발환경 세팅(DevContainer) 정보를 동시에 포함하고 있습니다. 빠른 개발환경을 위해서는 GitHub의 Codespace 기반으로 개발 환경을 구축하고, 웹브라우저 상에서 Visual Stduio Code IDE와 동일하게 개발하고 테스트 할 수 있습니다. 

- [Retrieval Augmented Generation(RAG) 실습 소개 영상](https://youtu.be/XsqPjHYZD04)
>별도의 프로그래밍 지식이 없더라도 나의 데이터를 조회하고 답변을 만들 수 있는 서비스를 만들 수 있습니다. 임베딩 되어 있는 Wikipedia 문서를 벡터DB에 색인화하고, Azure OpenAI의 On your data 기능으로 Playground에서 챗봇 서비스를 즉시 생성하는 방법을 설명합니다. OpenAI에서 제공하는 text-embedding-ada-002 API 기반으로 사전에 Wikipedia 정보를 Vector화 한 데이터의 일부분을 Azure AI Search 서비스에 인덱싱하고, Azure OpenAI Studio Playground 에서 on your data 로 연결하여 챗봇 서비스를 즉시 활용할 수 있는 방법을 다룹니다.

- [LLMOps Prompt Flow 영상](https://youtu.be/ECl0D8rHoDc)
>LLMOps를 위한 도구인 Prompt Flow를 설명하고, 질문을 하면, 위 영상에서 색인화된 벡터DB를 조회하여 원하는 답변을 생성하는 RAG 기반의 API를 생성하고 테스트 하는 방법을 소개합니다.
원활한 실습을 위해서 https://github.com/HyounsooKim/promptflow-kr 리포지토리를 활용하는 것을 추천 드립니다. GitHub Codespace 기반으로 실습 환경을 구축하고 시작할 수 있습니다.

----

## 실습에 사용하는 GPT 버전
현재 여기의 샘플은 주로 GPT 3.5를 기반으로 합니다. 일반적으로 gpt-35-turbo 최신 모델을 활용합니다. OpenAI의 모델 정책에 맞추어 Chat Completion API 기반으로 실습할 수 있습니다. gpt-35-turbo(0125) 모델 또는 gpt-4-turbo(0125-preview) 최신 모델을 활용하는 것을 추천 드립니다. (2024-03-17 기준)

## 설정하기
>안전한 로컬 환경에서의 키관리를 위해 실습에 필요한 API Endpoint 또는 API Key는 ***.env*** 파일을 활용하는 것을 강력히 추천합니다. 예를 들어 [.env.sample](./.env.sample) 파일을 복사하여 `.env` 파일을 만들고 해당 API KEY 정보를 입력하여 사용합니다.

----

# 개발환경 선택하기
>해당 실습을 원활하게 제공하기 위해서 .devcontainer 환경을 제공하고 있습니다. 나의 PC에 Docker나 IDE 설치를 원하지 않는다면, `CodeSpace`를 권장합니다. 
- Local PC에 `Docker`가 설치되어 있다면, VS Code에서 Reopen DevContainer를 실행하여 Docker에 컨테이너 이미지를 생성하면 자동으로 실습 가능한 런타임과 패키지들이 설치되도록 구성되어 있습니다.
- GitHub에서 제공하는 `CodeSpace`를 활용하면, CodeSpace가 제공하는 리모트 VM에 컨테이너가 올라가고, CodeSpace가 제공하는 웹브라우저 용 VS Code를 통해 즉시 개발을 진행할 수 있습니다.

참고: `CodeSpace`는 GitHub 개인 계정에게 월 15GB의 저장공간과 120 시간/core의 VM을 무료로 제공합니다. [자세한 가격 정보 참고는 클릭](https://docs.github.com/en/billing/managing-billing-for-github-codespaces/about-billing-for-github-codespaces)

## Contributing
We welcome contributions to this repository. If you have any ideas or suggestions, please feel free to open an issue or submit a pull request.

As technologies changes very fast, we endevour to keep this repository updated as quick as possible. However, this is heavily rely on keen community contributors to make this happen.

## Solution Accelerators
- **Business Process Automation:**
   - https://github.com/Azure/business-process-automation
   
- **Azure Cognitive Search + OpenAI**
   - https://github.com/Azure-Samples/azure-search-openai-demo

- **PowerApp + OpenAI**
   - https://github.com/Azure/azure-openai-samples/tree/main/solution_accelerators/PowerApp
   
- **Azure SQL Datbase + OpenAI**
   - https://github.com/louis-li/SqlGPT

- **ChatGPT + Enterprise data with Azure OpenAI**
   - https://github.com/lordlinus/Enterprise-ChatGPT

- **Azure OpenAI Semantic Search Demo | Document Upload**
   - https://github.com/MaheshSQL/openai-vector-search-demo

- **Redis + OpenAI**
   - https://github.com/louis-li/pdfGPT

## Relevant Repositories
- **OpenAI Cookbook**
   -  https://github.com/openai/openai-cookbook

- **Call center solutions:**
   - https://github.com/jakeatmsft/AzureOpenAIExamples/blob/main/Examples/Speech/Conversation_SSML%20OpenAI.ipynb 
   - https://github.com/amulchapla/AI-Powered-Call-Center-Intelligence 

- **Income Statement Analysis:**
   - https://github.com/jakeatmsft/AzureOpenAIExamples/blob/main/Examples/FormRecognizer/Balance_sheet_analysis.ipynb 
