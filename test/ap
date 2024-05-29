pip install streamlit openai

import streamlit as st
import openai

# OpenAI API Key를 입력 받는 함수
@st.cache
def get_openai_api_key():
    api_key = st.text_input("OpenAI API Key를 입력하세요", type="password")
    return api_key

# OpenAI API 인증
def authenticate_openai_api():
    api_key = get_openai_api_key()
    openai.api_key = api_key

# 사용자 입력을 받아 GPT-3.5-turbo 모델로 요청을 보내고 응답을 반환하는 함수
@st.cache(suppress_st_warning=True)
def get_gpt_response(prompt):
    response = openai.Completion.create(
        engine="text-davinci-003",
        prompt=prompt,
        max_tokens=150
    )
    return response.choices[0].text.strip()

# 메인 함수
def main():
    st.title("GPT-3.5-turbo 웹 앱")

    # OpenAI API 인증
    authenticate_openai_api()

    # 사용자 질문 입력
    user_input = st.text_area("질문을 입력하세요")

    if st.button("답변 받기"):
        # GPT-3.5-turbo 모델로 요청 보내고 응답 받기
        if user_input:
            response = get_gpt_response(user_input)
            st.write("답변:")
            st.write(response)
        else:
            st.warning("질문을 입력하세요.")

if __name__ == "__main__":
    main()
