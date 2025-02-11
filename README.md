# RAiD2
import streamlit as st

# アプリのタイトル
st.title("RAiD - 関節リウマチ治療薬提案AI")

# ユーザー入力（患者情報）
st.header("📝 患者情報を入力してください")
age = st.number_input("年齢", min_value=0, max_value=120, value=50)
gender = st.radio("性別", ["男性", "女性"])
disease_activity = st.selectbox("疾患活動性", ["低", "中", "高"])
current_treatment = st.text_input("現在の治療薬（一般名で入力）")

# 治療薬提案ロジック（仮）
def recommend_treatment(age, gender, disease_activity, current_treatment):
    if disease_activity == "高":
        return "バリシチニブ（JAK阻害剤）が推奨される可能性があります。"
    elif disease_activity == "中":
        return "IL-6阻害剤（トシリズマブなど）が有効かもしれません。"
    else:
        return "現在の治療を継続することを検討してください。"

# ボタンを押したら治療薬を提案
if st.button("治療薬を提案"):
    recommendation = recommend_treatment(age, gender, disease_activity, current_treatment)
    st.success(f"💡 推奨治療薬: {recommendation}")

# フィードバック欄
st.header("📝 フィードバック")
st.text_area("RAiDを使用した感想や改善点を入力してください")
