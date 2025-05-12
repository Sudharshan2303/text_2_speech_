import streamlit as st
from gtts import gTTS
import os
from io import BytesIO

def text_to_speech(text, language='en'):
    try:
        tts = gTTS(text=text, lang=language, slow=False)
        audio_bytes = BytesIO()
        tts.write_to_fp(audio_bytes)
        audio_bytes.seek(0)
        return audio_bytes
    except Exception as e:
        st.error(f"Error in text-to-speech conversion: {str(e)}")
        return None

def main():
    st.title("Text2Speech Converter")
    
    # Text input
    text = st.text_area("Enter text to convert to speech:", height=150)
    
    # Language selection
    language = st.selectbox(
        "Select language:",
        ('en', 'es', 'fr', 'de', 'it', 'ja', 'ko', 'zh-cn', 'hi'),
        index=0
    )
    
    if st.button("Convert to Speech"):
        if text.strip() == "":
            st.warning("Please enter some text to convert.")
        else:
            with st.spinner("Generating speech..."):
                audio_bytes = text_to_speech(text, language)
                if audio_bytes:
                    st.audio(audio_bytes, format='audio/mp3')
                    st.success("Conversion complete!")

if __name__ == "__main__":
    main()
