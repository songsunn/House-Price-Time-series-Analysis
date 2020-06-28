# House-price-Visualization
아파트 매매 가격 데이터를 활용한 시각화
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "9xRFvuEXeMAN"
   },
   "source": [
    "# 전국 신규 민간 아파트 분양가격 동향\n",
    "2013년부터 최근까지 부동산 가격 변동 추세 알아보기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "0am9HKneeMAN"
   },
   "outputs": [],
   "source": [
    "# 판다스 라이브러리 불러오기\n",
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "61_Nn8IbeMAQ",
    "outputId": "87b05b6f-5bf5-42ed-f773-ba0b4f8ab2dc"
   },
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "지정된 파일을 찾을 수 없습니다.\n"
     ]
    }
   ],
   "source": [
    "!move \"C:\\Users\\박미선\\Downloads\\주택도시보증공사_전국 평균 분양가격(2020년 2월) (1).csv\""
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "5l9ilSo-eMAT",
    "outputId": "590828ff-aca2-4435-f278-e1d2de8e6767"
   },
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "지정된 파일을 찾을 수 없습니다.\n"
     ]
    }
   ],
   "source": [
    "!move \"C:\\Users\\박미선\\Downloads\\전국 평균 분양가격(2013년 9월부터 2015년 8월까지) (1).csv"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "PgGBxqN1eMAW",
    "outputId": "30332b47-dbe6-47f5-8a5a-0c073bb63999"
   },
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "지정된 파일을 찾을 수 없습니다.\n"
     ]
    }
   ],
   "source": [
    "%ls C:\\jupyter notebookt\\data analystic"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "VXq8Yxv2eMAY"
   },
   "source": [
    "# 데이터 로드(주택도시보증공사)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "n2Rjeg0feMAY",
    "scrolled": true
   },
   "outputs": [],
   "source": [
    "# 데이터 로드\n",
    "# 한글 때문에 인코딩이 꺠져서, 인코딩 다시 설정(utf-8 or cp949)\n",
    "\n",
    "df_last=pd.read_csv(\"\\jupyter notebook\\data\\주택도시보증공사_전국 평균 분양가격(2020년 2월) (1).csv\",encoding=\"cp949\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "iDYIkZqNeMAb",
    "outputId": "f8b9c06a-47a5-4744-d820-175ef61ee5a0"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(4505, 5)"
      ]
     },
     "execution_count": 18,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "eXvKvr5leMAe",
    "outputId": "d73d0b10-80b5-4ab6-c162-599362a7fa21"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>규모구분</th>\n",
       "      <th>연도</th>\n",
       "      <th>월</th>\n",
       "      <th>분양가격(㎡)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>전체</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5841</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 60㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5652</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 60㎡초과 85㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5882</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 85㎡초과 102㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5721</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 102㎡초과</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5879</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  지역명               규모구분    연도   월 분양가격(㎡)\n",
       "0  서울                 전체  2015  10    5841\n",
       "1  서울         전용면적 60㎡이하  2015  10    5652\n",
       "2  서울   전용면적 60㎡초과 85㎡이하  2015  10    5882\n",
       "3  서울  전용면적 85㎡초과 102㎡이하  2015  10    5721\n",
       "4  서울        전용면적 102㎡초과  2015  10    5879"
      ]
     },
     "execution_count": 19,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "Z8wdKXpPeMAg",
    "outputId": "81ab2dea-7cee-45e5-8f0f-e00e818e239e"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>규모구분</th>\n",
       "      <th>연도</th>\n",
       "      <th>월</th>\n",
       "      <th>분양가격(㎡)</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>4500</th>\n",
       "      <td>제주</td>\n",
       "      <td>전체</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3955</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4501</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 60㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>4039</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4502</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 60㎡초과 85㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3962</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4503</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 85㎡초과 102㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>NaN</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4504</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 102㎡초과</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3601</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "     지역명               규모구분    연도  월 분양가격(㎡)\n",
       "4500  제주                 전체  2020  2    3955\n",
       "4501  제주         전용면적 60㎡이하  2020  2    4039\n",
       "4502  제주   전용면적 60㎡초과 85㎡이하  2020  2    3962\n",
       "4503  제주  전용면적 85㎡초과 102㎡이하  2020  2     NaN\n",
       "4504  제주        전용면적 102㎡초과  2020  2    3601"
      ]
     },
     "execution_count": 20,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# 결측치 1개 확인\n",
    "\n",
    "df_last.tail()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "QZ8SHhI5eMAi"
   },
   "source": [
    "# 데이터 로드(전국평균분양가격)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "PwWtqxTgeMAi",
    "outputId": "8c3b9969-5151-4fa6-febe-8e0f6cf453a3"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      " C 드라이브의 볼륨에는 이름이 없습니다."
     ]
    },
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "파일을 찾을 수 없습니다.\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      " 볼륨 일련 번호: AAB7-CA91\n",
      "\n",
      " C:\\jupyter_project 디렉터리\n",
      "\n"
     ]
    }
   ],
   "source": [
    "%ls C:\\jupyter_project\\data"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "VJWd-vvOeMAk"
   },
   "outputs": [],
   "source": [
    "df_first=pd.read_csv(\"\\jupyter notebook\\data\\전국 평균 분양가격(2013년 9월부터 2015년 8월까지) (1).csv\",encoding=\"cp949\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "xNGXNucjeMAm",
    "outputId": "8da37373-9a35-40ea-eaa2-98cf692d8fba"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(17, 22)"
      ]
     },
     "execution_count": 30,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_first.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "nmvqrEeXeMAo",
    "outputId": "16046af5-9460-4af9-893e-4773539d3fbe"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역</th>\n",
       "      <th>2013년12월</th>\n",
       "      <th>2014년1월</th>\n",
       "      <th>2014년2월</th>\n",
       "      <th>2014년3월</th>\n",
       "      <th>2014년4월</th>\n",
       "      <th>2014년5월</th>\n",
       "      <th>2014년6월</th>\n",
       "      <th>2014년7월</th>\n",
       "      <th>2014년8월</th>\n",
       "      <th>...</th>\n",
       "      <th>2014년11월</th>\n",
       "      <th>2014년12월</th>\n",
       "      <th>2015년1월</th>\n",
       "      <th>2015년2월</th>\n",
       "      <th>2015년3월</th>\n",
       "      <th>2015년4월</th>\n",
       "      <th>2015년5월</th>\n",
       "      <th>2015년6월</th>\n",
       "      <th>2015년7월</th>\n",
       "      <th>2015년8월</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>18189</td>\n",
       "      <td>17925</td>\n",
       "      <td>17925</td>\n",
       "      <td>18016</td>\n",
       "      <td>18098</td>\n",
       "      <td>19446</td>\n",
       "      <td>18867</td>\n",
       "      <td>18742</td>\n",
       "      <td>19274</td>\n",
       "      <td>...</td>\n",
       "      <td>20242</td>\n",
       "      <td>20269</td>\n",
       "      <td>20670</td>\n",
       "      <td>20670</td>\n",
       "      <td>19415</td>\n",
       "      <td>18842</td>\n",
       "      <td>18367</td>\n",
       "      <td>18374</td>\n",
       "      <td>18152</td>\n",
       "      <td>18443</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>부산</td>\n",
       "      <td>8111</td>\n",
       "      <td>8111</td>\n",
       "      <td>9078</td>\n",
       "      <td>8965</td>\n",
       "      <td>9402</td>\n",
       "      <td>9501</td>\n",
       "      <td>9453</td>\n",
       "      <td>9457</td>\n",
       "      <td>9411</td>\n",
       "      <td>...</td>\n",
       "      <td>9208</td>\n",
       "      <td>9208</td>\n",
       "      <td>9204</td>\n",
       "      <td>9235</td>\n",
       "      <td>9279</td>\n",
       "      <td>9327</td>\n",
       "      <td>9345</td>\n",
       "      <td>9515</td>\n",
       "      <td>9559</td>\n",
       "      <td>9581</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>대구</td>\n",
       "      <td>8080</td>\n",
       "      <td>8080</td>\n",
       "      <td>8077</td>\n",
       "      <td>8101</td>\n",
       "      <td>8267</td>\n",
       "      <td>8274</td>\n",
       "      <td>8360</td>\n",
       "      <td>8360</td>\n",
       "      <td>8370</td>\n",
       "      <td>...</td>\n",
       "      <td>8439</td>\n",
       "      <td>8253</td>\n",
       "      <td>8327</td>\n",
       "      <td>8416</td>\n",
       "      <td>8441</td>\n",
       "      <td>8446</td>\n",
       "      <td>8568</td>\n",
       "      <td>8542</td>\n",
       "      <td>8542</td>\n",
       "      <td>8795</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>인천</td>\n",
       "      <td>10204</td>\n",
       "      <td>10204</td>\n",
       "      <td>10408</td>\n",
       "      <td>10408</td>\n",
       "      <td>10000</td>\n",
       "      <td>9844</td>\n",
       "      <td>10058</td>\n",
       "      <td>9974</td>\n",
       "      <td>9973</td>\n",
       "      <td>...</td>\n",
       "      <td>10020</td>\n",
       "      <td>10020</td>\n",
       "      <td>10017</td>\n",
       "      <td>9876</td>\n",
       "      <td>9876</td>\n",
       "      <td>9938</td>\n",
       "      <td>10551</td>\n",
       "      <td>10443</td>\n",
       "      <td>10443</td>\n",
       "      <td>10449</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>광주</td>\n",
       "      <td>6098</td>\n",
       "      <td>7326</td>\n",
       "      <td>7611</td>\n",
       "      <td>7346</td>\n",
       "      <td>7346</td>\n",
       "      <td>7523</td>\n",
       "      <td>7659</td>\n",
       "      <td>7612</td>\n",
       "      <td>7622</td>\n",
       "      <td>...</td>\n",
       "      <td>7752</td>\n",
       "      <td>7748</td>\n",
       "      <td>7752</td>\n",
       "      <td>7756</td>\n",
       "      <td>7861</td>\n",
       "      <td>7914</td>\n",
       "      <td>7877</td>\n",
       "      <td>7881</td>\n",
       "      <td>8089</td>\n",
       "      <td>8231</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>5 rows × 22 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   지역  2013년12월  2014년1월  2014년2월  2014년3월  2014년4월  2014년5월  2014년6월  \\\n",
       "0  서울     18189    17925    17925    18016    18098    19446    18867   \n",
       "1  부산      8111     8111     9078     8965     9402     9501     9453   \n",
       "2  대구      8080     8080     8077     8101     8267     8274     8360   \n",
       "3  인천     10204    10204    10408    10408    10000     9844    10058   \n",
       "4  광주      6098     7326     7611     7346     7346     7523     7659   \n",
       "\n",
       "   2014년7월  2014년8월  ...  2014년11월  2014년12월  2015년1월  2015년2월  2015년3월  \\\n",
       "0    18742    19274  ...     20242     20269    20670    20670    19415   \n",
       "1     9457     9411  ...      9208      9208     9204     9235     9279   \n",
       "2     8360     8370  ...      8439      8253     8327     8416     8441   \n",
       "3     9974     9973  ...     10020     10020    10017     9876     9876   \n",
       "4     7612     7622  ...      7752      7748     7752     7756     7861   \n",
       "\n",
       "   2015년4월  2015년5월  2015년6월  2015년7월  2015년8월  \n",
       "0    18842    18367    18374    18152    18443  \n",
       "1     9327     9345     9515     9559     9581  \n",
       "2     8446     8568     8542     8542     8795  \n",
       "3     9938    10551    10443    10443    10449  \n",
       "4     7914     7877     7881     8089     8231  \n",
       "\n",
       "[5 rows x 22 columns]"
      ]
     },
     "execution_count": 31,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_first.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "sURCj9uGeMAq",
    "outputId": "bd8b8466-8954-4e72-86c1-dab1580bae0a"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역</th>\n",
       "      <th>2013년12월</th>\n",
       "      <th>2014년1월</th>\n",
       "      <th>2014년2월</th>\n",
       "      <th>2014년3월</th>\n",
       "      <th>2014년4월</th>\n",
       "      <th>2014년5월</th>\n",
       "      <th>2014년6월</th>\n",
       "      <th>2014년7월</th>\n",
       "      <th>2014년8월</th>\n",
       "      <th>...</th>\n",
       "      <th>2014년11월</th>\n",
       "      <th>2014년12월</th>\n",
       "      <th>2015년1월</th>\n",
       "      <th>2015년2월</th>\n",
       "      <th>2015년3월</th>\n",
       "      <th>2015년4월</th>\n",
       "      <th>2015년5월</th>\n",
       "      <th>2015년6월</th>\n",
       "      <th>2015년7월</th>\n",
       "      <th>2015년8월</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>12</th>\n",
       "      <td>전북</td>\n",
       "      <td>6282</td>\n",
       "      <td>6281</td>\n",
       "      <td>5946</td>\n",
       "      <td>5966</td>\n",
       "      <td>6277</td>\n",
       "      <td>6306</td>\n",
       "      <td>6351</td>\n",
       "      <td>6319</td>\n",
       "      <td>6436</td>\n",
       "      <td>...</td>\n",
       "      <td>6583</td>\n",
       "      <td>6583</td>\n",
       "      <td>6583</td>\n",
       "      <td>6583</td>\n",
       "      <td>6542</td>\n",
       "      <td>6551</td>\n",
       "      <td>6556</td>\n",
       "      <td>6601</td>\n",
       "      <td>6750</td>\n",
       "      <td>6580</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>13</th>\n",
       "      <td>전남</td>\n",
       "      <td>5678</td>\n",
       "      <td>5678</td>\n",
       "      <td>5678</td>\n",
       "      <td>5696</td>\n",
       "      <td>5736</td>\n",
       "      <td>5656</td>\n",
       "      <td>5609</td>\n",
       "      <td>5780</td>\n",
       "      <td>5685</td>\n",
       "      <td>...</td>\n",
       "      <td>5768</td>\n",
       "      <td>5784</td>\n",
       "      <td>5784</td>\n",
       "      <td>5833</td>\n",
       "      <td>5825</td>\n",
       "      <td>5940</td>\n",
       "      <td>6050</td>\n",
       "      <td>6243</td>\n",
       "      <td>6286</td>\n",
       "      <td>6289</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>14</th>\n",
       "      <td>경북</td>\n",
       "      <td>6168</td>\n",
       "      <td>6168</td>\n",
       "      <td>6234</td>\n",
       "      <td>6317</td>\n",
       "      <td>6412</td>\n",
       "      <td>6409</td>\n",
       "      <td>6554</td>\n",
       "      <td>6556</td>\n",
       "      <td>6563</td>\n",
       "      <td>...</td>\n",
       "      <td>6881</td>\n",
       "      <td>6989</td>\n",
       "      <td>6992</td>\n",
       "      <td>6953</td>\n",
       "      <td>6997</td>\n",
       "      <td>7006</td>\n",
       "      <td>6966</td>\n",
       "      <td>6887</td>\n",
       "      <td>7035</td>\n",
       "      <td>7037</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>15</th>\n",
       "      <td>경남</td>\n",
       "      <td>6473</td>\n",
       "      <td>6485</td>\n",
       "      <td>6502</td>\n",
       "      <td>6610</td>\n",
       "      <td>6599</td>\n",
       "      <td>6610</td>\n",
       "      <td>6615</td>\n",
       "      <td>6613</td>\n",
       "      <td>6606</td>\n",
       "      <td>...</td>\n",
       "      <td>7125</td>\n",
       "      <td>7332</td>\n",
       "      <td>7592</td>\n",
       "      <td>7588</td>\n",
       "      <td>7668</td>\n",
       "      <td>7683</td>\n",
       "      <td>7717</td>\n",
       "      <td>7715</td>\n",
       "      <td>7723</td>\n",
       "      <td>7665</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>16</th>\n",
       "      <td>제주</td>\n",
       "      <td>7674</td>\n",
       "      <td>7900</td>\n",
       "      <td>7900</td>\n",
       "      <td>7900</td>\n",
       "      <td>7900</td>\n",
       "      <td>7900</td>\n",
       "      <td>7914</td>\n",
       "      <td>7914</td>\n",
       "      <td>7914</td>\n",
       "      <td>...</td>\n",
       "      <td>7724</td>\n",
       "      <td>7739</td>\n",
       "      <td>7739</td>\n",
       "      <td>7739</td>\n",
       "      <td>7826</td>\n",
       "      <td>7285</td>\n",
       "      <td>7285</td>\n",
       "      <td>7343</td>\n",
       "      <td>7343</td>\n",
       "      <td>7343</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>5 rows × 22 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "    지역  2013년12월  2014년1월  2014년2월  2014년3월  2014년4월  2014년5월  2014년6월  \\\n",
       "12  전북      6282     6281     5946     5966     6277     6306     6351   \n",
       "13  전남      5678     5678     5678     5696     5736     5656     5609   \n",
       "14  경북      6168     6168     6234     6317     6412     6409     6554   \n",
       "15  경남      6473     6485     6502     6610     6599     6610     6615   \n",
       "16  제주      7674     7900     7900     7900     7900     7900     7914   \n",
       "\n",
       "    2014년7월  2014년8월  ...  2014년11월  2014년12월  2015년1월  2015년2월  2015년3월  \\\n",
       "12     6319     6436  ...      6583      6583     6583     6583     6542   \n",
       "13     5780     5685  ...      5768      5784     5784     5833     5825   \n",
       "14     6556     6563  ...      6881      6989     6992     6953     6997   \n",
       "15     6613     6606  ...      7125      7332     7592     7588     7668   \n",
       "16     7914     7914  ...      7724      7739     7739     7739     7826   \n",
       "\n",
       "    2015년4월  2015년5월  2015년6월  2015년7월  2015년8월  \n",
       "12     6551     6556     6601     6750     6580  \n",
       "13     5940     6050     6243     6286     6289  \n",
       "14     7006     6966     6887     7035     7037  \n",
       "15     7683     7717     7715     7723     7665  \n",
       "16     7285     7285     7343     7343     7343  \n",
       "\n",
       "[5 rows x 22 columns]"
      ]
     },
     "execution_count": 32,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_first.tail()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "zhlAiPGmeMAs",
    "outputId": "d9712ac1-5e92-4829-cce5-020a58ac0343"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 4505 entries, 0 to 4504\n",
      "Data columns (total 5 columns):\n",
      " #   Column   Non-Null Count  Dtype \n",
      "---  ------   --------------  ----- \n",
      " 0   지역명      4505 non-null   object\n",
      " 1   규모구분     4505 non-null   object\n",
      " 2   연도       4505 non-null   int64 \n",
      " 3   월        4505 non-null   int64 \n",
      " 4   분양가격(㎡)  4210 non-null   object\n",
      "dtypes: int64(2), object(3)\n",
      "memory usage: 176.1+ KB\n"
     ]
    }
   ],
   "source": [
    "#분양가격 컬럼만 다른 index 수 -> 결측치\n",
    "# object(문자형)->int64 or float64 수치형으로 바꿔줄 필요 있음\n",
    "\n",
    "df_last.info() "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "FaoBYGRqeMAu"
   },
   "source": [
    "# 결측치 보기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "hXxyIc_1eMAu",
    "outputId": "f4fca8d1-8b4f-4ef7-f237-eeafe226ff80"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "지역명          0\n",
       "규모구분         0\n",
       "연도           0\n",
       "월            0\n",
       "분양가격(㎡)    295\n",
       "dtype: int64"
      ]
     },
     "execution_count": 34,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# TRUE==1 FALSE==0\n",
    "# 분양가격 컬럼에 295개의 결측치가 있음을 확인\n",
    "\n",
    "df_last.isnull().sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "mV4Q8u4ceMAw",
    "outputId": "3f4ed046-f900-4c51-ac07-73f720b79137"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "지역명          0\n",
       "규모구분         0\n",
       "연도           0\n",
       "월            0\n",
       "분양가격(㎡)    295\n",
       "dtype: int64"
      ]
     },
     "execution_count": 35,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.isna().sum()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "zyWV1W5feMAy"
   },
   "source": [
    "# 데이터 타입 변경\n",
    "* 문자열 타입은 계산할 수 없기 때문에 수치 데이터로 변경"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "YMMWP4EpeMAz",
    "outputId": "20105528-b18a-446b-f07f-59219de0aec3"
   },
   "outputs": [
    {
     "ename": "ValueError",
     "evalue": "invalid literal for int() with base 10: '  '",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mValueError\u001b[0m                                Traceback (most recent call last)",
      "\u001b[1;32m<ipython-input-14-4021d990b8bd>\u001b[0m in \u001b[0;36m<module>\u001b[1;34m\u001b[0m\n\u001b[0;32m      1\u001b[0m \u001b[1;31m#공백문자가 있으면 stream데이터로 인식해서 int로 바꾸는데 문제가 생김\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m      2\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m----> 3\u001b[1;33m \u001b[0mdf_last\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;34m\"분양가격(㎡)\"\u001b[0m\u001b[1;33m]\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mastype\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mint\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\core\\generic.py\u001b[0m in \u001b[0;36mastype\u001b[1;34m(self, dtype, copy, errors)\u001b[0m\n\u001b[0;32m   5696\u001b[0m         \u001b[1;32melse\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   5697\u001b[0m             \u001b[1;31m# else, only a single dtype is given\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m-> 5698\u001b[1;33m             \u001b[0mnew_data\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_data\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mastype\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mdtype\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mdtype\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcopy\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mcopy\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0merrors\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0merrors\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m   5699\u001b[0m             \u001b[1;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_constructor\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mnew_data\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m__finalize__\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   5700\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\core\\internals\\managers.py\u001b[0m in \u001b[0;36mastype\u001b[1;34m(self, dtype, copy, errors)\u001b[0m\n\u001b[0;32m    580\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    581\u001b[0m     \u001b[1;32mdef\u001b[0m \u001b[0mastype\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mdtype\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcopy\u001b[0m\u001b[1;33m:\u001b[0m \u001b[0mbool\u001b[0m \u001b[1;33m=\u001b[0m \u001b[1;32mFalse\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0merrors\u001b[0m\u001b[1;33m:\u001b[0m \u001b[0mstr\u001b[0m \u001b[1;33m=\u001b[0m \u001b[1;34m\"raise\"\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 582\u001b[1;33m         \u001b[1;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mapply\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;34m\"astype\"\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mdtype\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mdtype\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcopy\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mcopy\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0merrors\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0merrors\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    583\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    584\u001b[0m     \u001b[1;32mdef\u001b[0m \u001b[0mconvert\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m,\u001b[0m \u001b[1;33m**\u001b[0m\u001b[0mkwargs\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\core\\internals\\managers.py\u001b[0m in \u001b[0;36mapply\u001b[1;34m(self, f, filter, **kwargs)\u001b[0m\n\u001b[0;32m    440\u001b[0m                 \u001b[0mapplied\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mb\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mapply\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mf\u001b[0m\u001b[1;33m,\u001b[0m \u001b[1;33m**\u001b[0m\u001b[0mkwargs\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    441\u001b[0m             \u001b[1;32melse\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 442\u001b[1;33m                 \u001b[0mapplied\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mgetattr\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mb\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mf\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;33m**\u001b[0m\u001b[0mkwargs\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    443\u001b[0m             \u001b[0mresult_blocks\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0m_extend_blocks\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mapplied\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mresult_blocks\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    444\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\core\\internals\\blocks.py\u001b[0m in \u001b[0;36mastype\u001b[1;34m(self, dtype, copy, errors)\u001b[0m\n\u001b[0;32m    623\u001b[0m             \u001b[0mvals1d\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mvalues\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mravel\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    624\u001b[0m             \u001b[1;32mtry\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 625\u001b[1;33m                 \u001b[0mvalues\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mastype_nansafe\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mvals1d\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mdtype\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mcopy\u001b[0m\u001b[1;33m=\u001b[0m\u001b[1;32mTrue\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    626\u001b[0m             \u001b[1;32mexcept\u001b[0m \u001b[1;33m(\u001b[0m\u001b[0mValueError\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mTypeError\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    627\u001b[0m                 \u001b[1;31m# e.g. astype_nansafe can fail on object-dtype of strings\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\core\\dtypes\\cast.py\u001b[0m in \u001b[0;36mastype_nansafe\u001b[1;34m(arr, dtype, copy, skipna)\u001b[0m\n\u001b[0;32m    872\u001b[0m         \u001b[1;31m# work around NumPy brokenness, #1987\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    873\u001b[0m         \u001b[1;32mif\u001b[0m \u001b[0mnp\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0missubdtype\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mdtype\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mtype\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mnp\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0minteger\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 874\u001b[1;33m             \u001b[1;32mreturn\u001b[0m \u001b[0mlib\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mastype_intsafe\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0marr\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mravel\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mdtype\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mreshape\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0marr\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mshape\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    875\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    876\u001b[0m         \u001b[1;31m# if we have a datetime/timedelta array of objects\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mpandas\\_libs\\lib.pyx\u001b[0m in \u001b[0;36mpandas._libs.lib.astype_intsafe\u001b[1;34m()\u001b[0m\n",
      "\u001b[1;31mValueError\u001b[0m: invalid literal for int() with base 10: '  '"
     ]
    }
   ],
   "source": [
    "#공백문자가 있으면 stream데이터로 인식해서 int로 바꾸는데 문제가 생김\n",
    "\n",
    "df_last[\"분양가격(㎡)\"].astype(int)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "mkia7lSVeMA3"
   },
   "outputs": [],
   "source": [
    "import numpy as np"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "pdUev7q0eMA4",
    "outputId": "329a7ce7-d6f3-4589-e2b1-7c0b12074109"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "float"
      ]
     },
     "execution_count": 6,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "type(np.nan)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "AW_RwGkDeMA6"
   },
   "outputs": [],
   "source": [
    "#  errors='raise' -> invalid하면 에러를 출력\n",
    "#  errors='coerce' -> 에러 무시하고 강제로 출력\n",
    "# 데이터타입 float64\n",
    "\n",
    "df_last[\"분양가격\"]=pd.to_numeric(df_last[\"분양가격(㎡)\"],  errors='coerce')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "A9KBxLQseMA8",
    "outputId": "ce4bce55-1330-4702-9a06-0102cf02fa1b",
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0       5841.0\n",
       "1       5652.0\n",
       "2       5882.0\n",
       "3       5721.0\n",
       "4       5879.0\n",
       "         ...  \n",
       "4500    3955.0\n",
       "4501    4039.0\n",
       "4502    3962.0\n",
       "4503       NaN\n",
       "4504    3601.0\n",
       "Name: 분양가격, Length: 4505, dtype: float64"
      ]
     },
     "execution_count": 16,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#원본은 그대로 두고, 컬럼만 바꿈\n",
    "\n",
    "df_last[\"분양가격\"]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "fYvlB4_SeMA-"
   },
   "source": [
    "# 평균분당가격 구하기\n",
    "* 전국평균분양 데이터는 평당분양가격 기준으로 되어 있음\n",
    "* 분양가격을 평당분양가격으로 보기 위해서는 3.3을 곱해야 한다"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "r2EStO7FeMA-"
   },
   "outputs": [],
   "source": [
    "df_last[\"평당분양가격\"]=df_last[\"분양가격\"]*3.3"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "xl3qVWwseMBA",
    "outputId": "4e19d738-39f3-4420-f24e-af00bfb00b0f"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 4505 entries, 0 to 4504\n",
      "Data columns (total 7 columns):\n",
      " #   Column   Non-Null Count  Dtype  \n",
      "---  ------   --------------  -----  \n",
      " 0   지역명      4505 non-null   object \n",
      " 1   규모구분     4505 non-null   object \n",
      " 2   연도       4505 non-null   int64  \n",
      " 3   월        4505 non-null   int64  \n",
      " 4   분양가격(㎡)  4210 non-null   object \n",
      " 5   분양가격     4109 non-null   float64\n",
      " 6   평당분양가격   4109 non-null   float64\n",
      "dtypes: float64(2), int64(2), object(3)\n",
      "memory usage: 246.5+ KB\n"
     ]
    }
   ],
   "source": [
    "df_last.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "vOBJJHwdeMBB"
   },
   "source": [
    "## 분양가격 데이터 요약하기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "ZOeCiUYIeMBC",
    "outputId": "a7ac2f0e-865f-4cc3-88a1-d8426339d87b"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "count     4210\n",
       "unique    1795\n",
       "top       2221\n",
       "freq        17\n",
       "Name: 분양가격(㎡), dtype: object"
      ]
     },
     "execution_count": 20,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#  분양가격(㎡) 컬럼 요약\n",
    "#  object(문자형)은 결측치도 데이터로 처리 \n",
    "#  unique-> 중복되지 않은 값.범주형이나 문자형 데이터 요약할 때 참고. \n",
    "#  top-> 가장 빈번하게 등장하는 문자\n",
    "#  freq-> 가장 빈번하게 등장하는 문자가 몇번 등장하는지(2221 문자가 17번 등장한다)\n",
    "    \n",
    "df_last[\"분양가격(㎡)\"].describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "5TWkmANBeMBD",
    "outputId": "0b5c374a-a3e6-448f-9145-4ebfe1fd47d4"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "count     4109.000000\n",
       "mean      3260.909467\n",
       "std       1289.733449\n",
       "min       1868.000000\n",
       "25%       2453.000000\n",
       "50%       2887.000000\n",
       "75%       3594.000000\n",
       "max      13835.000000\n",
       "Name: 분양가격, dtype: float64"
      ]
     },
     "execution_count": 21,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# 수치 데이터로 변경된 분양가격 컬럼 요약\n",
    "# 숫자는 공백을 결측치로 표시하여, 위의 값과 다름\n",
    "\n",
    "# 75%값에 비해 최댓값이 매우 크다. \n",
    "# 중앙값과 평균값의 차이. 중앙값보다 평균이 훨씬 크다-> 최댓값 때문\n",
    "\n",
    "df_last[\"분양가격\"].describe()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "8mArwzaHeMBF"
   },
   "source": [
    "# 규모구분을 전용면적 컬럼으로 변경\n",
    "* 규모구분 컬럼에서 전용면적, 초과, 이하 등의 문구를 빼고 간결하게 만들기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "HuPuHEz3eMBG",
    "outputId": "8f27a48f-881c-4ca9-a003-e32bebfe97f0"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "array(['전체', '전용면적 60㎡이하', '전용면적 60㎡초과 85㎡이하', '전용면적 85㎡초과 102㎡이하',\n",
       "       '전용면적 102㎡초과'], dtype=object)"
      ]
     },
     "execution_count": 22,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#모든 행에 다 들어가는 전용면적으로 이름을 바꾸면, 불필요한 데이터 줄일 수 있음\n",
    "\n",
    "df_last[\"규모구분\"].unique()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "aduUaGB6eMBI",
    "outputId": "72c00669-7ca5-458e-a885-a5b58cda06a5"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0                  전체\n",
       "1               60㎡이하\n",
       "2         60㎡초과 85㎡이하\n",
       "3        85㎡초과 102㎡이하\n",
       "4              102㎡초과\n",
       "            ...      \n",
       "4500               전체\n",
       "4501            60㎡이하\n",
       "4502      60㎡초과 85㎡이하\n",
       "4503     85㎡초과 102㎡이하\n",
       "4504           102㎡초과\n",
       "Name: 전용면적, Length: 4505, dtype: object"
      ]
     },
     "execution_count": 23,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# 전용면적 단어 제거\n",
    "# 초과, 이하 단어를 물결표시(~)로 바꿈\n",
    "\n",
    "df_last[\"전용면적\"]=df_last[\"규모구분\"].str.replace(\"전용면적\",\"\")\n",
    "df_last[\"전용면적\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "uzzBNGtyeMBJ",
    "outputId": "18410f8d-8716-4401-e2a2-32802aadd35b"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0               전체\n",
       "1              60㎡\n",
       "2         60㎡~ 85㎡\n",
       "3        85㎡~ 102㎡\n",
       "4            102㎡~\n",
       "           ...    \n",
       "4500            전체\n",
       "4501           60㎡\n",
       "4502      60㎡~ 85㎡\n",
       "4503     85㎡~ 102㎡\n",
       "4504         102㎡~\n",
       "Name: 전용면적, Length: 4505, dtype: object"
      ]
     },
     "execution_count": 24,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last[\"전용면적\"]=df_last[\"전용면적\"].str.replace(\"초과\",\"~\")\n",
    "df_last[\"전용면적\"]=df_last[\"전용면적\"].str.replace(\"이하\",\"\")\n",
    "df_last[\"전용면적\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "aOzE0oareMBL",
    "outputId": "0a48f914-cdbc-4893-efe7-eca420248010"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0             전체\n",
       "1            60㎡\n",
       "2        60㎡~85㎡\n",
       "3       85㎡~102㎡\n",
       "4          102㎡~\n",
       "          ...   \n",
       "4500          전체\n",
       "4501         60㎡\n",
       "4502     60㎡~85㎡\n",
       "4503    85㎡~102㎡\n",
       "4504       102㎡~\n",
       "Name: 전용면적, Length: 4505, dtype: object"
      ]
     },
     "execution_count": 25,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# 공백도 제거\n",
    "# 앞뒤에 있는 공백 제거\n",
    "\n",
    "df_last[\"전용면적\"]=df_last[\"전용면적\"].str.replace(\" \",\"\").str.strip()\n",
    "df_last[\"전용면적\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "VZVw7DaZeMBN",
    "outputId": "cab550e3-cff1-4ecc-8c8b-3fa999be85a7"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>규모구분</th>\n",
       "      <th>연도</th>\n",
       "      <th>월</th>\n",
       "      <th>분양가격(㎡)</th>\n",
       "      <th>분양가격</th>\n",
       "      <th>평당분양가격</th>\n",
       "      <th>전용면적</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>전체</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5841</td>\n",
       "      <td>5841.0</td>\n",
       "      <td>19275.3</td>\n",
       "      <td>전체</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 60㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5652</td>\n",
       "      <td>5652.0</td>\n",
       "      <td>18651.6</td>\n",
       "      <td>60㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 60㎡초과 85㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5882</td>\n",
       "      <td>5882.0</td>\n",
       "      <td>19410.6</td>\n",
       "      <td>60㎡~85㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 85㎡초과 102㎡이하</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5721</td>\n",
       "      <td>5721.0</td>\n",
       "      <td>18879.3</td>\n",
       "      <td>85㎡~102㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>서울</td>\n",
       "      <td>전용면적 102㎡초과</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5879</td>\n",
       "      <td>5879.0</td>\n",
       "      <td>19400.7</td>\n",
       "      <td>102㎡~</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4500</th>\n",
       "      <td>제주</td>\n",
       "      <td>전체</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3955</td>\n",
       "      <td>3955.0</td>\n",
       "      <td>13051.5</td>\n",
       "      <td>전체</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4501</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 60㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>4039</td>\n",
       "      <td>4039.0</td>\n",
       "      <td>13328.7</td>\n",
       "      <td>60㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4502</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 60㎡초과 85㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3962</td>\n",
       "      <td>3962.0</td>\n",
       "      <td>13074.6</td>\n",
       "      <td>60㎡~85㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4503</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 85㎡초과 102㎡이하</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>NaN</td>\n",
       "      <td>85㎡~102㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4504</th>\n",
       "      <td>제주</td>\n",
       "      <td>전용면적 102㎡초과</td>\n",
       "      <td>2020</td>\n",
       "      <td>2</td>\n",
       "      <td>3601</td>\n",
       "      <td>3601.0</td>\n",
       "      <td>11883.3</td>\n",
       "      <td>102㎡~</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>4505 rows × 8 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     지역명               규모구분    연도   월 분양가격(㎡)    분양가격   평당분양가격      전용면적\n",
       "0     서울                 전체  2015  10    5841  5841.0  19275.3        전체\n",
       "1     서울         전용면적 60㎡이하  2015  10    5652  5652.0  18651.6       60㎡\n",
       "2     서울   전용면적 60㎡초과 85㎡이하  2015  10    5882  5882.0  19410.6   60㎡~85㎡\n",
       "3     서울  전용면적 85㎡초과 102㎡이하  2015  10    5721  5721.0  18879.3  85㎡~102㎡\n",
       "4     서울        전용면적 102㎡초과  2015  10    5879  5879.0  19400.7     102㎡~\n",
       "...   ..                ...   ...  ..     ...     ...      ...       ...\n",
       "4500  제주                 전체  2020   2    3955  3955.0  13051.5        전체\n",
       "4501  제주         전용면적 60㎡이하  2020   2    4039  4039.0  13328.7       60㎡\n",
       "4502  제주   전용면적 60㎡초과 85㎡이하  2020   2    3962  3962.0  13074.6   60㎡~85㎡\n",
       "4503  제주  전용면적 85㎡초과 102㎡이하  2020   2     NaN     NaN      NaN  85㎡~102㎡\n",
       "4504  제주        전용면적 102㎡초과  2020   2    3601  3601.0  11883.3     102㎡~\n",
       "\n",
       "[4505 rows x 8 columns]"
      ]
     },
     "execution_count": 26,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "wAuX55S-eMBP"
   },
   "outputs": [],
   "source": [
    "#axis=0 -> 행\n",
    "#axis=1 -> 열\n",
    "\n",
    "df_last=df_last.drop([\"규모구분\",\"분양가격(㎡)\"],axis=1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "OVZmtvcKeMBQ",
    "outputId": "eaf6c073-074b-4d32-c8ef-cf16f8dcdd3f"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 4505 entries, 0 to 4504\n",
      "Data columns (total 6 columns):\n",
      " #   Column  Non-Null Count  Dtype  \n",
      "---  ------  --------------  -----  \n",
      " 0   지역명     4505 non-null   object \n",
      " 1   연도      4505 non-null   int64  \n",
      " 2   월       4505 non-null   int64  \n",
      " 3   분양가격    4109 non-null   float64\n",
      " 4   평당분양가격  4109 non-null   float64\n",
      " 5   전용면적    4505 non-null   object \n",
      "dtypes: float64(2), int64(2), object(2)\n",
      "memory usage: 211.3+ KB\n"
     ]
    }
   ],
   "source": [
    "df_last.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "OGRsa6nMeMBS",
    "outputId": "cb5d0a22-700b-48a5-bfbb-d32ded61a0f5"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>연도</th>\n",
       "      <th>월</th>\n",
       "      <th>분양가격</th>\n",
       "      <th>평당분양가격</th>\n",
       "      <th>전용면적</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5841.0</td>\n",
       "      <td>19275.3</td>\n",
       "      <td>전체</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5652.0</td>\n",
       "      <td>18651.6</td>\n",
       "      <td>60㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5882.0</td>\n",
       "      <td>19410.6</td>\n",
       "      <td>60㎡~85㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5721.0</td>\n",
       "      <td>18879.3</td>\n",
       "      <td>85㎡~102㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5879.0</td>\n",
       "      <td>19400.7</td>\n",
       "      <td>102㎡~</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  지역명    연도   월    분양가격   평당분양가격      전용면적\n",
       "0  서울  2015  10  5841.0  19275.3        전체\n",
       "1  서울  2015  10  5652.0  18651.6       60㎡\n",
       "2  서울  2015  10  5882.0  19410.6   60㎡~85㎡\n",
       "3  서울  2015  10  5721.0  18879.3  85㎡~102㎡\n",
       "4  서울  2015  10  5879.0  19400.7     102㎡~"
      ]
     },
     "execution_count": 29,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "6elRhyyieMBU"
   },
   "source": [
    "# 데이터 집계하기\n",
    "\n",
    "* 지역명으로 분양가격의 평균 구하고, 막대그래프로 시각화하기\n",
    "* 연도, 월별 분양가격 확인\n",
    "* df.groupby([\"인덱스로 사용할 컬럼명\"])[\"계산할 컬럼값\"].연산()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "DQB8i-IAeMBU",
    "outputId": "d73d139e-4649-41a4-ebec-c7f6f3a6ffce"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "지역명\n",
       "강원     7964.589286\n",
       "경기    13463.657308\n",
       "경남     9292.592941\n",
       "경북     8407.034940\n",
       "광주    10073.984211\n",
       "대구    12090.296429\n",
       "대전    10343.193204\n",
       "부산    12137.196923\n",
       "서울    23876.121923\n",
       "세종     9861.693061\n",
       "울산    10038.387097\n",
       "인천    11989.170703\n",
       "전남     7601.511328\n",
       "전북     7754.411628\n",
       "제주    11297.426432\n",
       "충남     8265.784337\n",
       "충북     7651.430769\n",
       "Name: 평당분양가격, dtype: float64"
      ]
     },
     "execution_count": 31,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#지역명에 따른 평단분양가격의 평균\n",
    "\n",
    "df_last.groupby([\"지역명\"])[\"평당분양가격\"].mean()\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "qwDuErcJeMBV",
    "outputId": "303d7e01-24b9-4403-d0bb-dd46f5fc204d"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "전용면적\n",
       "102㎡~       11602.832552\n",
       "60㎡         10435.698663\n",
       "60㎡~85㎡     10332.899657\n",
       "85㎡~102㎡    11214.679034\n",
       "전체          10338.911314\n",
       "Name: 평당분양가격, dtype: float64"
      ]
     },
     "execution_count": 32,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#전용면적에 따른 평단분양가격의 평균\n",
    "\n",
    "df_last.groupby([\"전용면적\"])[\"평당분양가격\"].mean()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "dEKA3pfpeMBX",
    "outputId": "748c5446-4943-47c9-aaaa-1a774f245009"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th>지역명</th>\n",
       "      <th>강원</th>\n",
       "      <th>경기</th>\n",
       "      <th>경남</th>\n",
       "      <th>경북</th>\n",
       "      <th>광주</th>\n",
       "      <th>대구</th>\n",
       "      <th>대전</th>\n",
       "      <th>부산</th>\n",
       "      <th>서울</th>\n",
       "      <th>세종</th>\n",
       "      <th>울산</th>\n",
       "      <th>인천</th>\n",
       "      <th>전남</th>\n",
       "      <th>전북</th>\n",
       "      <th>제주</th>\n",
       "      <th>충남</th>\n",
       "      <th>충북</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전용면적</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>102㎡~</th>\n",
       "      <td>8487.0</td>\n",
       "      <td>14860.0</td>\n",
       "      <td>10358.0</td>\n",
       "      <td>9199.0</td>\n",
       "      <td>11205.0</td>\n",
       "      <td>13233.0</td>\n",
       "      <td>14875.0</td>\n",
       "      <td>13249.0</td>\n",
       "      <td>23675.0</td>\n",
       "      <td>10217.0</td>\n",
       "      <td>9974.0</td>\n",
       "      <td>14432.0</td>\n",
       "      <td>8242.0</td>\n",
       "      <td>8217.0</td>\n",
       "      <td>10578.0</td>\n",
       "      <td>8715.0</td>\n",
       "      <td>8202.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡</th>\n",
       "      <td>7601.0</td>\n",
       "      <td>13368.0</td>\n",
       "      <td>8709.0</td>\n",
       "      <td>7907.0</td>\n",
       "      <td>9581.0</td>\n",
       "      <td>12078.0</td>\n",
       "      <td>9285.0</td>\n",
       "      <td>11391.0</td>\n",
       "      <td>23369.0</td>\n",
       "      <td>9324.0</td>\n",
       "      <td>9332.0</td>\n",
       "      <td>11315.0</td>\n",
       "      <td>7254.0</td>\n",
       "      <td>7638.0</td>\n",
       "      <td>13988.0</td>\n",
       "      <td>7910.0</td>\n",
       "      <td>7131.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡~85㎡</th>\n",
       "      <td>7513.0</td>\n",
       "      <td>12601.0</td>\n",
       "      <td>8676.0</td>\n",
       "      <td>8107.0</td>\n",
       "      <td>10020.0</td>\n",
       "      <td>11886.0</td>\n",
       "      <td>9791.0</td>\n",
       "      <td>11907.0</td>\n",
       "      <td>22943.0</td>\n",
       "      <td>9830.0</td>\n",
       "      <td>10492.0</td>\n",
       "      <td>11459.0</td>\n",
       "      <td>7307.0</td>\n",
       "      <td>7304.0</td>\n",
       "      <td>10716.0</td>\n",
       "      <td>7854.0</td>\n",
       "      <td>7282.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85㎡~102㎡</th>\n",
       "      <td>8851.0</td>\n",
       "      <td>13842.0</td>\n",
       "      <td>10044.0</td>\n",
       "      <td>8774.0</td>\n",
       "      <td>9296.0</td>\n",
       "      <td>11244.0</td>\n",
       "      <td>9037.0</td>\n",
       "      <td>12167.0</td>\n",
       "      <td>26632.0</td>\n",
       "      <td>9915.0</td>\n",
       "      <td>8861.0</td>\n",
       "      <td>11589.0</td>\n",
       "      <td>7909.0</td>\n",
       "      <td>8310.0</td>\n",
       "      <td>10709.0</td>\n",
       "      <td>9189.0</td>\n",
       "      <td>8403.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전체</th>\n",
       "      <td>7508.0</td>\n",
       "      <td>12648.0</td>\n",
       "      <td>8714.0</td>\n",
       "      <td>8125.0</td>\n",
       "      <td>10010.0</td>\n",
       "      <td>11880.0</td>\n",
       "      <td>9871.0</td>\n",
       "      <td>11973.0</td>\n",
       "      <td>22762.0</td>\n",
       "      <td>9867.0</td>\n",
       "      <td>10487.0</td>\n",
       "      <td>11337.0</td>\n",
       "      <td>7320.0</td>\n",
       "      <td>7325.0</td>\n",
       "      <td>10872.0</td>\n",
       "      <td>7848.0</td>\n",
       "      <td>7240.0</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "지역명           강원       경기       경남      경북       광주       대구       대전  \\\n",
       "전용면적                                                                    \n",
       "102㎡~     8487.0  14860.0  10358.0  9199.0  11205.0  13233.0  14875.0   \n",
       "60㎡       7601.0  13368.0   8709.0  7907.0   9581.0  12078.0   9285.0   \n",
       "60㎡~85㎡   7513.0  12601.0   8676.0  8107.0  10020.0  11886.0   9791.0   \n",
       "85㎡~102㎡  8851.0  13842.0  10044.0  8774.0   9296.0  11244.0   9037.0   \n",
       "전체        7508.0  12648.0   8714.0  8125.0  10010.0  11880.0   9871.0   \n",
       "\n",
       "지역명            부산       서울       세종       울산       인천      전남      전북  \\\n",
       "전용면적                                                                    \n",
       "102㎡~     13249.0  23675.0  10217.0   9974.0  14432.0  8242.0  8217.0   \n",
       "60㎡       11391.0  23369.0   9324.0   9332.0  11315.0  7254.0  7638.0   \n",
       "60㎡~85㎡   11907.0  22943.0   9830.0  10492.0  11459.0  7307.0  7304.0   \n",
       "85㎡~102㎡  12167.0  26632.0   9915.0   8861.0  11589.0  7909.0  8310.0   \n",
       "전체        11973.0  22762.0   9867.0  10487.0  11337.0  7320.0  7325.0   \n",
       "\n",
       "지역명            제주      충남      충북  \n",
       "전용면적                               \n",
       "102㎡~     10578.0  8715.0  8202.0  \n",
       "60㎡       13988.0  7910.0  7131.0  \n",
       "60㎡~85㎡   10716.0  7854.0  7282.0  \n",
       "85㎡~102㎡  10709.0  9189.0  8403.0  \n",
       "전체        10872.0  7848.0  7240.0  "
      ]
     },
     "execution_count": 33,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#지역명, 전용면적에 따른 평당분양가격의 평균\n",
    "# unstack() -> 두번째 인덱스가 컬럼값으로 온다\n",
    "\n",
    "df_last.groupby([\"전용면적\",\"지역명\"])[\"평당분양가격\"].mean().unstack().round()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "RNRdCv7-eMBZ",
    "outputId": "78cfb858-3742-415f-f7c6-9ca9e93c8781"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th>연도</th>\n",
       "      <th>2015</th>\n",
       "      <th>2016</th>\n",
       "      <th>2017</th>\n",
       "      <th>2018</th>\n",
       "      <th>2019</th>\n",
       "      <th>2020</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>지역명</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>강원</th>\n",
       "      <td>7188.060</td>\n",
       "      <td>7162.903846</td>\n",
       "      <td>7273.560000</td>\n",
       "      <td>8219.255000</td>\n",
       "      <td>8934.475000</td>\n",
       "      <td>9751.500</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경기</th>\n",
       "      <td>11060.940</td>\n",
       "      <td>11684.970000</td>\n",
       "      <td>12304.980000</td>\n",
       "      <td>14258.420000</td>\n",
       "      <td>15665.540000</td>\n",
       "      <td>16132.710</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경남</th>\n",
       "      <td>8459.220</td>\n",
       "      <td>8496.730000</td>\n",
       "      <td>8786.760000</td>\n",
       "      <td>9327.670000</td>\n",
       "      <td>10697.615789</td>\n",
       "      <td>10027.875</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경북</th>\n",
       "      <td>7464.160</td>\n",
       "      <td>7753.405000</td>\n",
       "      <td>8280.800000</td>\n",
       "      <td>8680.776923</td>\n",
       "      <td>9050.250000</td>\n",
       "      <td>9325.800</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>광주</th>\n",
       "      <td>7916.700</td>\n",
       "      <td>9190.683333</td>\n",
       "      <td>9613.977551</td>\n",
       "      <td>9526.953333</td>\n",
       "      <td>12111.675000</td>\n",
       "      <td>13150.500</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대구</th>\n",
       "      <td>9018.900</td>\n",
       "      <td>10282.030000</td>\n",
       "      <td>12206.700000</td>\n",
       "      <td>12139.252632</td>\n",
       "      <td>14081.650000</td>\n",
       "      <td>14737.800</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대전</th>\n",
       "      <td>8190.600</td>\n",
       "      <td>8910.733333</td>\n",
       "      <td>9957.158491</td>\n",
       "      <td>10234.106667</td>\n",
       "      <td>12619.200000</td>\n",
       "      <td>12567.225</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>부산</th>\n",
       "      <td>10377.400</td>\n",
       "      <td>10743.535000</td>\n",
       "      <td>11560.680000</td>\n",
       "      <td>12889.965000</td>\n",
       "      <td>13537.865000</td>\n",
       "      <td>13389.090</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>서울</th>\n",
       "      <td>20315.680</td>\n",
       "      <td>21753.435000</td>\n",
       "      <td>21831.060000</td>\n",
       "      <td>23202.245000</td>\n",
       "      <td>28286.830000</td>\n",
       "      <td>30779.760</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>세종</th>\n",
       "      <td>8765.020</td>\n",
       "      <td>8857.805000</td>\n",
       "      <td>9132.505556</td>\n",
       "      <td>10340.463158</td>\n",
       "      <td>11299.394118</td>\n",
       "      <td>11792.550</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>울산</th>\n",
       "      <td>9367.600</td>\n",
       "      <td>9582.574138</td>\n",
       "      <td>10666.935714</td>\n",
       "      <td>10241.400000</td>\n",
       "      <td>10216.250000</td>\n",
       "      <td>10621.600</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>인천</th>\n",
       "      <td>10976.020</td>\n",
       "      <td>11099.055000</td>\n",
       "      <td>11640.600000</td>\n",
       "      <td>11881.532143</td>\n",
       "      <td>13249.775000</td>\n",
       "      <td>13805.880</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전남</th>\n",
       "      <td>6798.880</td>\n",
       "      <td>6936.600000</td>\n",
       "      <td>7372.920000</td>\n",
       "      <td>7929.845000</td>\n",
       "      <td>8219.275862</td>\n",
       "      <td>8723.550</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전북</th>\n",
       "      <td>7110.400</td>\n",
       "      <td>6906.625000</td>\n",
       "      <td>7398.973585</td>\n",
       "      <td>8174.595000</td>\n",
       "      <td>8532.260000</td>\n",
       "      <td>8502.780</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>제주</th>\n",
       "      <td>7951.075</td>\n",
       "      <td>9567.480000</td>\n",
       "      <td>12566.730000</td>\n",
       "      <td>11935.968000</td>\n",
       "      <td>11828.469231</td>\n",
       "      <td>12834.525</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충남</th>\n",
       "      <td>7689.880</td>\n",
       "      <td>7958.225000</td>\n",
       "      <td>8198.422222</td>\n",
       "      <td>8201.820000</td>\n",
       "      <td>8748.840000</td>\n",
       "      <td>9033.750</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충북</th>\n",
       "      <td>6828.800</td>\n",
       "      <td>7133.335000</td>\n",
       "      <td>7473.120000</td>\n",
       "      <td>8149.295000</td>\n",
       "      <td>7970.875000</td>\n",
       "      <td>8070.810</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "연도        2015          2016          2017          2018          2019  \\\n",
       "지역명                                                                      \n",
       "강원    7188.060   7162.903846   7273.560000   8219.255000   8934.475000   \n",
       "경기   11060.940  11684.970000  12304.980000  14258.420000  15665.540000   \n",
       "경남    8459.220   8496.730000   8786.760000   9327.670000  10697.615789   \n",
       "경북    7464.160   7753.405000   8280.800000   8680.776923   9050.250000   \n",
       "광주    7916.700   9190.683333   9613.977551   9526.953333  12111.675000   \n",
       "대구    9018.900  10282.030000  12206.700000  12139.252632  14081.650000   \n",
       "대전    8190.600   8910.733333   9957.158491  10234.106667  12619.200000   \n",
       "부산   10377.400  10743.535000  11560.680000  12889.965000  13537.865000   \n",
       "서울   20315.680  21753.435000  21831.060000  23202.245000  28286.830000   \n",
       "세종    8765.020   8857.805000   9132.505556  10340.463158  11299.394118   \n",
       "울산    9367.600   9582.574138  10666.935714  10241.400000  10216.250000   \n",
       "인천   10976.020  11099.055000  11640.600000  11881.532143  13249.775000   \n",
       "전남    6798.880   6936.600000   7372.920000   7929.845000   8219.275862   \n",
       "전북    7110.400   6906.625000   7398.973585   8174.595000   8532.260000   \n",
       "제주    7951.075   9567.480000  12566.730000  11935.968000  11828.469231   \n",
       "충남    7689.880   7958.225000   8198.422222   8201.820000   8748.840000   \n",
       "충북    6828.800   7133.335000   7473.120000   8149.295000   7970.875000   \n",
       "\n",
       "연도        2020  \n",
       "지역명             \n",
       "강원    9751.500  \n",
       "경기   16132.710  \n",
       "경남   10027.875  \n",
       "경북    9325.800  \n",
       "광주   13150.500  \n",
       "대구   14737.800  \n",
       "대전   12567.225  \n",
       "부산   13389.090  \n",
       "서울   30779.760  \n",
       "세종   11792.550  \n",
       "울산   10621.600  \n",
       "인천   13805.880  \n",
       "전남    8723.550  \n",
       "전북    8502.780  \n",
       "제주   12834.525  \n",
       "충남    9033.750  \n",
       "충북    8070.810  "
      ]
     },
     "execution_count": 34,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#연도,지역명으로 평당분양가격의 평균 구하기\n",
    "# unstack().T -> 행과 열 바꾸기\n",
    "# 시각화하거나 재사용하기 위해 변수에 넣음\n",
    "\n",
    "g= df_last.groupby([\"연도\",\"지역명\"])[\"평당분양가격\"].mean()\n",
    "g.unstack().T"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "oV0gAL7MeMBb"
   },
   "source": [
    "## Pivot table로 데이터 집계하기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "0pPQF4bZeMBb",
    "outputId": "871a75a4-219e-4d94-b685-5df60cf1fdb8"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>지역명</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>강원</th>\n",
       "      <td>7964.589286</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경기</th>\n",
       "      <td>13463.657308</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경남</th>\n",
       "      <td>9292.592941</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경북</th>\n",
       "      <td>8407.034940</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>광주</th>\n",
       "      <td>10073.984211</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대구</th>\n",
       "      <td>12090.296429</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대전</th>\n",
       "      <td>10343.193204</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>부산</th>\n",
       "      <td>12137.196923</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>서울</th>\n",
       "      <td>23876.121923</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>세종</th>\n",
       "      <td>9861.693061</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>울산</th>\n",
       "      <td>10038.387097</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>인천</th>\n",
       "      <td>11989.170703</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전남</th>\n",
       "      <td>7601.511328</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전북</th>\n",
       "      <td>7754.411628</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>제주</th>\n",
       "      <td>11297.426432</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충남</th>\n",
       "      <td>8265.784337</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충북</th>\n",
       "      <td>7651.430769</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "           평당분양가격\n",
       "지역명              \n",
       "강원    7964.589286\n",
       "경기   13463.657308\n",
       "경남    9292.592941\n",
       "경북    8407.034940\n",
       "광주   10073.984211\n",
       "대구   12090.296429\n",
       "대전   10343.193204\n",
       "부산   12137.196923\n",
       "서울   23876.121923\n",
       "세종    9861.693061\n",
       "울산   10038.387097\n",
       "인천   11989.170703\n",
       "전남    7601.511328\n",
       "전북    7754.411628\n",
       "제주   11297.426432\n",
       "충남    8265.784337\n",
       "충북    7651.430769"
      ]
     },
     "execution_count": 35,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# aggfunc=\"mean\"이 디폴트값\n",
    "# groupby와 달리 데이터프레임으로 나옴.\n",
    "# pd.pivot은 연산 기능이 없다. \n",
    "\n",
    "pd.pivot_table(df_last, index=[\"지역명\"],values=[\"평당분양가격\"],aggfunc=\"mean\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "AI9TLTzteMBd",
    "outputId": "ef818de8-c6c0-4107-e2d0-52d55b71eed8"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전용면적</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>102㎡~</th>\n",
       "      <td>11602.832552</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡</th>\n",
       "      <td>10435.698663</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡~85㎡</th>\n",
       "      <td>10332.899657</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85㎡~102㎡</th>\n",
       "      <td>11214.679034</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전체</th>\n",
       "      <td>10338.911314</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                평당분양가격\n",
       "전용면적                  \n",
       "102㎡~     11602.832552\n",
       "60㎡       10435.698663\n",
       "60㎡~85㎡   10332.899657\n",
       "85㎡~102㎡  11214.679034\n",
       "전체        10338.911314"
      ]
     },
     "execution_count": 36,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "pd.pivot_table(df_last, index=[\"전용면적\"],values=[\"평당분양가격\"])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "zPM5bd6KeMBg",
    "outputId": "4fd91c17-36d6-4707-b545-6ae8d4384138"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전용면적</th>\n",
       "      <th>지역명</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th rowspan=\"5\" valign=\"top\">102㎡~</th>\n",
       "      <th>강원</th>\n",
       "      <td>8486.521154</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경기</th>\n",
       "      <td>14859.646154</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경남</th>\n",
       "      <td>10358.363265</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경북</th>\n",
       "      <td>9199.384615</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>광주</th>\n",
       "      <td>11204.684615</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th rowspan=\"5\" valign=\"top\">전체</th>\n",
       "      <th>전남</th>\n",
       "      <td>7320.161538</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전북</th>\n",
       "      <td>7325.365385</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>제주</th>\n",
       "      <td>10872.167308</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충남</th>\n",
       "      <td>7847.526923</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충북</th>\n",
       "      <td>7239.628846</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>85 rows × 1 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "                 평당분양가격\n",
       "전용면적  지역명              \n",
       "102㎡~ 강원    8486.521154\n",
       "      경기   14859.646154\n",
       "      경남   10358.363265\n",
       "      경북    9199.384615\n",
       "      광주   11204.684615\n",
       "...                 ...\n",
       "전체    전남    7320.161538\n",
       "      전북    7325.365385\n",
       "      제주   10872.167308\n",
       "      충남    7847.526923\n",
       "      충북    7239.628846\n",
       "\n",
       "[85 rows x 1 columns]"
      ]
     },
     "execution_count": 37,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "\n",
    "\n",
    "df_last.pivot_table(index=[\"전용면적\",\"지역명\"],values=[\"평당분양가격\"])"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "SKob6XFfeMBi",
    "outputId": "3335a2f2-64b7-4018-fa36-4540fb1eb40b"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th>지역명</th>\n",
       "      <th>강원</th>\n",
       "      <th>경기</th>\n",
       "      <th>경남</th>\n",
       "      <th>경북</th>\n",
       "      <th>광주</th>\n",
       "      <th>대구</th>\n",
       "      <th>대전</th>\n",
       "      <th>부산</th>\n",
       "      <th>서울</th>\n",
       "      <th>세종</th>\n",
       "      <th>울산</th>\n",
       "      <th>인천</th>\n",
       "      <th>전남</th>\n",
       "      <th>전북</th>\n",
       "      <th>제주</th>\n",
       "      <th>충남</th>\n",
       "      <th>충북</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전용면적</th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>102㎡~</th>\n",
       "      <td>8487.0</td>\n",
       "      <td>14860.0</td>\n",
       "      <td>10358.0</td>\n",
       "      <td>9199.0</td>\n",
       "      <td>11205.0</td>\n",
       "      <td>13233.0</td>\n",
       "      <td>14875.0</td>\n",
       "      <td>13249.0</td>\n",
       "      <td>23675.0</td>\n",
       "      <td>10217.0</td>\n",
       "      <td>9974.0</td>\n",
       "      <td>14432.0</td>\n",
       "      <td>8242.0</td>\n",
       "      <td>8217.0</td>\n",
       "      <td>10578.0</td>\n",
       "      <td>8715.0</td>\n",
       "      <td>8202.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡</th>\n",
       "      <td>7601.0</td>\n",
       "      <td>13368.0</td>\n",
       "      <td>8709.0</td>\n",
       "      <td>7907.0</td>\n",
       "      <td>9581.0</td>\n",
       "      <td>12078.0</td>\n",
       "      <td>9285.0</td>\n",
       "      <td>11391.0</td>\n",
       "      <td>23369.0</td>\n",
       "      <td>9324.0</td>\n",
       "      <td>9332.0</td>\n",
       "      <td>11315.0</td>\n",
       "      <td>7254.0</td>\n",
       "      <td>7638.0</td>\n",
       "      <td>13988.0</td>\n",
       "      <td>7910.0</td>\n",
       "      <td>7131.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60㎡~85㎡</th>\n",
       "      <td>7513.0</td>\n",
       "      <td>12601.0</td>\n",
       "      <td>8676.0</td>\n",
       "      <td>8107.0</td>\n",
       "      <td>10020.0</td>\n",
       "      <td>11886.0</td>\n",
       "      <td>9791.0</td>\n",
       "      <td>11907.0</td>\n",
       "      <td>22943.0</td>\n",
       "      <td>9830.0</td>\n",
       "      <td>10492.0</td>\n",
       "      <td>11459.0</td>\n",
       "      <td>7307.0</td>\n",
       "      <td>7304.0</td>\n",
       "      <td>10716.0</td>\n",
       "      <td>7854.0</td>\n",
       "      <td>7282.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85㎡~102㎡</th>\n",
       "      <td>8851.0</td>\n",
       "      <td>13842.0</td>\n",
       "      <td>10044.0</td>\n",
       "      <td>8774.0</td>\n",
       "      <td>9296.0</td>\n",
       "      <td>11244.0</td>\n",
       "      <td>9037.0</td>\n",
       "      <td>12167.0</td>\n",
       "      <td>26632.0</td>\n",
       "      <td>9915.0</td>\n",
       "      <td>8861.0</td>\n",
       "      <td>11589.0</td>\n",
       "      <td>7909.0</td>\n",
       "      <td>8310.0</td>\n",
       "      <td>10709.0</td>\n",
       "      <td>9189.0</td>\n",
       "      <td>8403.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전체</th>\n",
       "      <td>7508.0</td>\n",
       "      <td>12648.0</td>\n",
       "      <td>8714.0</td>\n",
       "      <td>8125.0</td>\n",
       "      <td>10010.0</td>\n",
       "      <td>11880.0</td>\n",
       "      <td>9871.0</td>\n",
       "      <td>11973.0</td>\n",
       "      <td>22762.0</td>\n",
       "      <td>9867.0</td>\n",
       "      <td>10487.0</td>\n",
       "      <td>11337.0</td>\n",
       "      <td>7320.0</td>\n",
       "      <td>7325.0</td>\n",
       "      <td>10872.0</td>\n",
       "      <td>7848.0</td>\n",
       "      <td>7240.0</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "지역명           강원       경기       경남      경북       광주       대구       대전  \\\n",
       "전용면적                                                                    \n",
       "102㎡~     8487.0  14860.0  10358.0  9199.0  11205.0  13233.0  14875.0   \n",
       "60㎡       7601.0  13368.0   8709.0  7907.0   9581.0  12078.0   9285.0   \n",
       "60㎡~85㎡   7513.0  12601.0   8676.0  8107.0  10020.0  11886.0   9791.0   \n",
       "85㎡~102㎡  8851.0  13842.0  10044.0  8774.0   9296.0  11244.0   9037.0   \n",
       "전체        7508.0  12648.0   8714.0  8125.0  10010.0  11880.0   9871.0   \n",
       "\n",
       "지역명            부산       서울       세종       울산       인천      전남      전북  \\\n",
       "전용면적                                                                    \n",
       "102㎡~     13249.0  23675.0  10217.0   9974.0  14432.0  8242.0  8217.0   \n",
       "60㎡       11391.0  23369.0   9324.0   9332.0  11315.0  7254.0  7638.0   \n",
       "60㎡~85㎡   11907.0  22943.0   9830.0  10492.0  11459.0  7307.0  7304.0   \n",
       "85㎡~102㎡  12167.0  26632.0   9915.0   8861.0  11589.0  7909.0  8310.0   \n",
       "전체        11973.0  22762.0   9867.0  10487.0  11337.0  7320.0  7325.0   \n",
       "\n",
       "지역명            제주      충남      충북  \n",
       "전용면적                               \n",
       "102㎡~     10578.0  8715.0  8202.0  \n",
       "60㎡       13988.0  7910.0  7131.0  \n",
       "60㎡~85㎡   10716.0  7854.0  7282.0  \n",
       "85㎡~102㎡  10709.0  9189.0  8403.0  \n",
       "전체        10872.0  7848.0  7240.0  "
      ]
     },
     "execution_count": 38,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.pivot_table(index=\"전용면적\",columns=\"지역명\",values=\"평당분양가격\").round()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "KIc8S6O8eMBk",
    "outputId": "bf70cc52-5609-4178-d303-0ea88d56b739"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>지역명</th>\n",
       "      <th></th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>강원</th>\n",
       "      <td>8219.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경기</th>\n",
       "      <td>14258.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경남</th>\n",
       "      <td>9328.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>경북</th>\n",
       "      <td>8681.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>광주</th>\n",
       "      <td>9527.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대구</th>\n",
       "      <td>12139.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>대전</th>\n",
       "      <td>10234.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>부산</th>\n",
       "      <td>12890.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>서울</th>\n",
       "      <td>23202.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>세종</th>\n",
       "      <td>10340.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>울산</th>\n",
       "      <td>10241.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>인천</th>\n",
       "      <td>11882.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전남</th>\n",
       "      <td>7930.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>전북</th>\n",
       "      <td>8175.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>제주</th>\n",
       "      <td>11936.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충남</th>\n",
       "      <td>8202.0</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>충북</th>\n",
       "      <td>8149.0</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "      평당분양가격\n",
       "지역명         \n",
       "강원    8219.0\n",
       "경기   14258.0\n",
       "경남    9328.0\n",
       "경북    8681.0\n",
       "광주    9527.0\n",
       "대구   12139.0\n",
       "대전   10234.0\n",
       "부산   12890.0\n",
       "서울   23202.0\n",
       "세종   10340.0\n",
       "울산   10241.0\n",
       "인천   11882.0\n",
       "전남    7930.0\n",
       "전북    8175.0\n",
       "제주   11936.0\n",
       "충남    8202.0\n",
       "충북    8149.0"
      ]
     },
     "execution_count": 39,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "p=df_last.pivot_table(index=[\"연도\",\"지역명\"],values=\"평당분양가격\").round()\n",
    "p.loc[2018]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "3NHe0OkzeMBn"
   },
   "source": [
    "# 시각화하기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "4LbN5_weeMBn",
    "outputId": "22e9c024-d9ce-4e01-fcff-6743423c8c81",
    "scrolled": false
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a40f780>"
      ]
     },
     "execution_count": 40,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x216 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# 지역명으로 분양가격의 평균 구하고, 선그래프 시각화\n",
    "# missing from current font.-> 폰트가 없어서 오류 발생\n",
    "# rot=0 은 글씨 회전/ figsize는 막대그래프 간격, 크기 설정\n",
    "# sort_values(ascending= False) -> 큰 순서대로 나열\n",
    "\n",
    "g= df_last.groupby([\"지역명\"])[\"평당분양가격\"].mean().sort_values(ascending=False)\n",
    "g.plot.bar(rot=0, figsize=(10,3))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "eet_yQJBeMBp"
   },
   "outputs": [],
   "source": [
    "# 한글폰트 지정\n",
    "\n",
    "import matplotlib.pyplot as plt\n",
    "\n",
    "plt.rc(\"font\",family=\"Gothic\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "yGiAcucteMBr",
    "outputId": "768e7360-398b-49da-a781-804f4e2820f9"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a367e80>"
      ]
     },
     "execution_count": 42,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#전용면적 별 평당분양가격\n",
    "\n",
    "df_last.groupby([\"전용면적\"])[\"평당분양가격\"].mean().plot.bar()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "iLRlyazseMBs",
    "outputId": "0def1df6-3c98-4a36-ab46-56365b55aedb"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a515470>"
      ]
     },
     "execution_count": 43,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAAYEAAAEGCAYAAACD7ClEAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjMsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+AADFEAAAgAElEQVR4nO3deXxU5dn/8c9FCDuEJSyyhF32TQZQxBW11LYo1VajdQEVW9tqW60VbZ9Ha/Wh2se2oFWpRKRqFRWt1KX2EUEQKgmKgiyyJOxbWMIaSDLX74850ZgfCEkmmUzm+369ePXMfc5MrhvsfHOue84cc3dERCQx1Yp1ASIiEjsKARGRBKYQEBFJYAoBEZEEphAQEUlgtWNdQFmlpqZ6p06dYl2GiEjcWLx4ca67tzzWvrgLgU6dOpGVlRXrMkRE4oaZrT/ePrWDREQSmEJARCSBKQRERBKYQkBEJIEpBEREEphCQEQkgSkEREQSmEJARKQac3fe/3wnT8xdWymvH3cXi4mIJAJ3571VO5j07hqWbNxL+2b1uX54J+olJ0X15ygERESqkXDYeWf5dh59bzXLNu+jfbP6PDimH5cNbkfd2tENAFAIiIhUC0Vh561lW3l09hpWbttPpxYNePjy/lw6qB3JSZXXuVcIiIjEUGFRmFmfbuHR2WtYu/Mg3Vo14k9XDOTb/U+hdiW++RdTCIiIxEBBUZhXP97MX95bQ86uQ/Rs05hHrxrEN/ueQlItq7I6FAIiIlXoSGERLy/exONz1rJpz2H6tmvCk9cM5sJeralVhW/+xRQCIiJVIL+giBczN/LE3LVszctnYIem/PaSPpzXoxVmVf/mX0whICJSiQ4fLeK5D9fz5Pvr2Ln/CEM6NeOhy/szoltqTN/8iykEREQqwYEjhfxt4XqemreOXQePMrxrCyZdOYjTuzSvFm/+xRQCIiJRlHe4gGcW5JDxQTZ7DxVw9qktufX8boQ6NY91acd0whAwsx7A08AGd7/SzFoCjwBpQENgmrs/ambnARlA8W3MFrv77WbWBJgKtAEOA+PcfZOZtQ2ObwjsBMa6e16U5yciUiX2HjpKxvxsnl6Qw/78Qi7o1YqfnN+dgR2axrq0r3UyZwLDgEnApcHjlsDv3X2ZmdUHss3sMaAp8Ii7Ty71/DuATHd/yMwuAR4G0oGJQIa7zzCz24C7gAkVn5KISNXZdeAIT83PZvqCHA4eLWJUnzb85Pxu9G2XEuvSTsoJQ8Ddp5vZuSUeLy+xuwWwyd3dzJoBN5nZlcAO4F53/wQYCVwdHD+LSKAAnAOMC7ZnAK+jEBCROLFjXz5T3l/Hcx9uIL+wiG/3b8tPzutGjzaNY11amZR7TcDMGgLTgRuDoWnunhHsGwG8ZmbdgFQgF8Ddw2aWZGa1gGR3Lwyem0vkDON4P2s8MB4gLS2tvCWLiFTY1rzDPDl3Hc8v2kBR2LlkQFtuOa8b3Vo1inVp5VKuEDCzxkR+e7/P3ZdA5A2+eL+7zzez3UBrYA+QAhwIdoeDMCgwM3N3D/bvOd7Pc/cpwBSAUCjk5alZRKQiNu4+xONz1/Jy1ibC7lx2WntuOa8rHVs0jHVpFVLmEDCzFGAmcL+7zy0x3g9YFrSG+gJ1gK3AfGA08LiZXQgsCZ6SCYwC3gLGAPMqMhERkcqQk3uQv8xZw8yPNlPLjO+F2vPDc7rSoXmDWJcWFeU5E7gH6AncW+KzrlcTWUD+q5kdAY4C6UEgTASmmVk6UADcHDznTmCqmU0A8vhyfUBEJObW7DjAY++t4R9LNpOcVIsfnN6Rm8/pwikp9WNdWlRZpBsTP0KhkGdlZcW6DBGpoVZt28/k2at5Y+lW6tVO4genp3HT2V1o1bherEsrNzNb7O6hY+3TxWIiIsCyzXlMnr2af322nYZ1kvjhOV25cURnWjSqG+vSKpVCQEQS2pKNe5n87mreXbmDxvVqc+v53Rg3ojNNG9SJdWlVQiEgIgkpK2c3k2av4f3Pd9K0QTK3X3gq1w7vREr95FiXVqUUAiKSMNyd/6zbzaR3V7Nw3S5aNKzDr0b15JozOtKobmK+HSbmrEUkobg781bnMnn2ajJz9tCycV1+/a1eXDUsjQZ1EvttMLFnLyI1mrsze+UOJs1ewycb93JKSj3uG92HK4Z0oF5yUqzLqxYUAiJS44TDzjvLtzN59mo+27KPdk3r88CYvlw+uD11a+vNvySFgIjUGEVh582lW3l09hpWbd9PxxYNeOjy/owZ1I7kpFqxLq9aUgiISNwrLAoz69MtPDp7DWt3HqRry4b88YoBfKd/W2rrzf9rKQREJG4VFIV59ePN/OW9NeTsOkSP1o159KpBfLPvKSTVqj63cKzOFAIiEneOFBbx8uJNPD5nLZv2HKZP2yY88YPBXNS7NbX05l8mCgERiSsL1uZy+4xP2JqXz4AOTblvdB/O79mqWt28PZ4oBEQkbizbnMdNz2TRJqUe08cN5azuqXrzryCFgIjEhQ27DnH905k0bVCH5286ndZN4vdbPasThYCIVHu7DhzhuqcXUVAU5oXxwxQAUaTPTolItXboaCHjpmWyZe9hMq4P0a1VfN3IvbpTCIhItVVQFObHz33E0s15TE4fxOCOzWNdUo2jdpCIVEvuzj2vLuW9VTt5cEw/LurTJtYl1Ug6ExCRaumRf3/OjKxN3DqyO1cNS4t1OTWWQkBEqp1n/7OeybPXcOWQDvz8gu6xLqdGO2EImFkPM1tgZi8Ej1ua2d/MbK6ZZZnZT4LxZDObYmbzzOx9M+sbjDcxs5eC8XfMrH0w3tbM3g7GZ5pZSmVOVETiw9vLtvFf/1jGyJ6t+N2lfXUdQCU7mTOBYcCkEo9bAr9393OAs4BfW+Rf6Rqg0N3PAm4FpgTH3wFkBuOPAQ8H4xOBjGB8LnBXRScjIvEtM2c3t77wMf3bN2XyVYP05W9V4IR/w+4+HdhW4vFyd18WPGwBbHJ3B0YCM4JjlgAtzKxhyXFgFjA82D4HmBlszwAuqNhURCSerd6+nxumZdK+aX0yrh+S8Hf8qirljtngDX46cGMwlArkljgkl8hZwxfj7h4GksysFpDs7oWljj3ezxoftJ6ydu7cWd6SRaSa2pp3mOsyFlE3OYlnxg2lecM6sS4pYZQrBMysMfAycF/wWz/AHqBkXz8lGCs9Hg7CoMC+bPYVH3tM7j7F3UPuHmrZ8rhZISJxKO9wAddnZLIvv5BpY4fQoXmDWJeUUMocAsEC7mtE1gXmltg1HxgdHNMDKHD3vFLjFwLFoZEJjAq2xwDzyjMBEYlf+QVFjJ+exbrcAzx5zWD6tNXnQ6paeZpu9wA9gXtLrNpfDUwFnjKzeUTCZXywbyIwzczSgQLg5mD8TmCqmU0A8oBx5ZqBiMSlorDzixlL+DB7N3++ciBndkuNdUkJySJruvEjFAp5VlZWrMsQkQpwd+6btZxpC3K45+Je3HR2l1iXVKOZ2WJ3Dx1rnz5/JSJV7om565i2IIcbR3RWAMSYQkBEqtTMjzbx+7dXMnpAW+6+uFesy0l4CgERqTJzP9/JnS9/yvCuLXj4e/11P+BqQCEgIlVi6aY8fvTsYrq3bsyT1wymbu2kWJckKAREpAqs33WQsdMW0axBHZ4ZO4TG9ZJjXZIEdF22iFSq3ANHuDZjEYVh58UbhtJKt4asVnQmICKV5uCRyK0ht+/LZ+p1Q+jaslGsS5JSFAIiUikKisLc8txHLNucx6PppzG4Y7NYlyTHoHaQiESdu3PXK0uZ+/lOJn63Hxf0bh3rkuQ4dCYgIlH3h3dW8cpHm/jZBd25cqhuDVmdKQREJKqmL8zhsffWkj60A7eN1K0hqzuFgIhEzVtLt/Lfr3/GBb1ac/8lujVkPFAIiEhULMrezW0vLmFQh6ZMTtetIeOF/pVEpMI+376fG5/JpEOz+ky9bgj16+hq4HihEBCRCtmyN3JryHrBrSGb6daQcUUhICLllneogOufXsSB/EKmjR1K+2a6NWS80XUCIlIu+QVF3DQ9i+zcgzwzdii92zaJdUlSDgoBESmzorDzsxeWsChnN5PSBzFct4aMW2oHiUiZRG4N+Rlvf7aN33y7N6MHtI11SVIBCgERKZO/zFnL9IXrGX92F24Y0TnW5UgFnTAEzKyHmS0wsxdKjA0xsxVmNrHE2Hlmlm1mc4I//xuMNzGzl8xsnpm9Y2btg/G2ZvZ2MD7TzFIqY4IiEj0vL97Ew/9axaUD23LXqJ6xLkei4GTOBIYBk0qNDQYeLzXWFHjE3c8N/twejN8BZLr7WcBjwMPB+EQgIxifC9xVngmISNV4b9UOfvXKp4zolspDlw/QrSFriBOGgLtPB7aVGnsC2Ffq0GbATWb2gZm9amYDgvGRwIxgexYwPNg+B5gZbM8ALih7+SJSFT7ZuJdbnv2IHq0b8/gPTqNObXWSa4pofjpomrtnAJjZCOA1M+sGpAK5AO4eNrMkM6sFJLt7YfDcXKDl8V7YzMYD4wHS0vSNhCJVKSf3IOOmZdKiUR2mjdOtIWuaqMW5u4dLbM8HdgOtgT1AyX5/ODi2wL78dqmU4LjjvfYUdw+5e6hly+NmhYhE2c79kVtDOjB93FBaNdatIWuaqIWAmfUrflM3s75AHWArMB8YHYxfCCwJnpIJjAq2xwDzolWLiFRc8a0hd+4/wtTrQnTRrSFrpGi2g4YBfzWzI8BRIN3dPfgE0TQzSwcKgJuD4+8EpprZBCAPGBfFWkSkAgqKwvzouY9YvnUff712MIPSdGvImsrcPdY1lEkoFPKsrKxYlyFSY7k7t8/4hJkfb+ahy/rz/SEdYl2SVJCZLXb30LH2aYlfRL7i92+vYubHm/nFhacqABKAQkBEvjDtg2yemLuWq4al8dPzu8W6HKkCCgERAeCNT7dy3z+Xc1Fv3RoykSgERIT/rNvFz19cwuC0ZkxKH0SSrgZOGAoBkQS3cts+bpqeRVqLBjx1XYh6ybo1ZCJRCIgksM17D3N9RiYN6kRuDdm0gW4NmWgUAiIJau+ho1yXsYiDRwp5ZtxQ2jWtH+uSJAZ0ZzGRBJRfUMSNz2SxYdchnhk3lJ5tdGvIRKUQEEkwRWHn1r9/zOINe5icPogzuraIdUkSQ2oHiSQQd+e/X1/GO8u381/f7s23++vWkIlOISCSQB57bw3P/mcDN5/ThbFn6taQohAQSRgzsjbyh3c+Z8ygdvzqG7o1pEQoBEQSwOyV25kwcylndU/l95f1160h5QsKAZEabsnGvfz4uY/pdUpjHv/BYN0aUr5C/zWI1GDrdh5g3LRMUhvXIeP6ITSqqw8EylcpBERqqB3787nu6UUATB83TLeGlGNSCIjUQAeCW0Pm7j9KxvVD6JzaMNYlSTWlc0ORGuZoYZgfPbuYFVv389R1IQZ2aBrrkqQa05mASA0SDjt3vvwJ81bnMvG7/TivR6tYlyTVnEJApAb5/dsreW3JFu646FS+F9KtIeXEThgCZtbDzBaY2QslxoaY2Qozm1hiLNnMppjZPDN738z6BuNNzOylYPwdM2sfjLc1s7eD8ZlmllIZExRJFBnzs3ny/XVcc3pHfnyebg0pJ+dkzgSGAZNKjQ0GHi81dg1Q6O5nAbcCU4LxO4DMYPwx4OFgfCKQEYzPBe4qe/kiAvDPT7dw/xvLGdWnDfeO7qNbQ8pJO2EIuPt0YFupsSeAfaUOHQnMCPYvAVqYWcOS48AsYHiwfQ4wM9ieAVxQjvpFEt6Ctbn84sVPCHVsxp+uHKhbQ0qZRHNNIBXILfE4F2hZctzdw0CSmdUCkt29sNSxx2Rm480sy8yydu7cGcWSReKXu/Ovz7Zx8/TFdGzRgKeuHaJbQ0qZRfMjonuAkn39lGCsePxAMB5297CZFZiZubuXOPaY3H0KQXspFAp5FGsWiUsrtu7j/n8uZ8HaXZzauhHTxg4lpUFyrMuSOBTNEJgPjAY+MLMeQIG755lZ8fjjZnYhsCQ4PhMYBbwFjAHmRbEWkRop98AR/vedz3kxcwNN6ifz20v6cNXQNGon6YN+Uj7RDIGpwFNmNo9Im2l8MD4RmGZm6UABcHMwficw1cwmAHnAuCjWIlKjHCks4pkFOUx+dw2HC4q4bngnfjbyVP32LxVmkW5M/AiFQp6VlRXrMkSqhLvz7+XbeeDNFazfdYjze7bi7ot70a1Vo1iXJnHEzBa7e+hY+/S1ESLVVMm+f7dWjXhm3FDOOfW4n58QKReFgEg1o76/VCWFgEg1ob6/xIJCQCTG3J13lm/nQfX9JQYUAiIxtGLrPn47azkL1+2iu/r+EgMKAZEYUN9fqguFgEgVOlJYxLQPcnh0dqTvf/3wztw2srv6/hIzCgGRKnCsvv893+pF15bq+0tsKQREKpn6/lKdKQREKon6/hIPFAIiUaa+v8QThYBIlKjvL/FIISASBer7S7xSCIhUQMm+f0r9ZO6/pA/p6vtLHFEIiJSD+v5SUygERMqgdN9/ZM9W3K2+v8QxhYDISVq+JfL9/gvXRe7rO33cUM5W31/inEJA5AQiff9VvJC5kabq+0sNoxAQOY7ivv/k2WvILyhirPr+UgMpBERKcXf+9Vmk779ht/r+UrOdMATMrAfwNLDB3a8Mxh4AzgMMmODuc8zsPCADWB88dbG7325mTYCpQBvgMDDO3TeZWdvg+IbATmCsu+dFd3oiZaO+vySakzkTGAZMAi4FMLPzgYHuPjx4I59tZn2BpsAj7j651PPvADLd/SEzuwR4GEgHJgIZ7j7DzG4D7gImRGVWImWkvr8kqhOGgLtPN7NzSwyNBF4K9m0xs/VAD6AZcJOZXQnsAO5190+C468OnjuLSKAAnAOMC7ZnAK+jEJAqVrrvP+7Mztx6vvr+kjjKsyaQCiws8TgXaAlMc/cMADMbAbxmZt2C43MB3D1sZklmVgtIdvfCUq9xTGY2HhgPkJaWVo6SRb7qWH3/e77Viy7q+0uCKU8I7AFSSjxOAfa4e7h4wN3nm9luoHWJ4w8Eu8NBGBSYmbm7F7/G8X6gu08BpgCEQiEvR80iX1DfX+RL5QmB+cA1wHNmlkqkFbTKzPoBy9zdgzWCOsDW4PjRwONmdiGwJHidTGAU8BYwBphXoZmInMD/1/e/tC/pQzqo7y8JrTwh8CZwkZktAGoBt7l7vpkNA/5qZkeAo0B6EAgTgWlmlg4UADcHr3MnMNXMJgB5fLk+IBJV6vuLHJ9FujHxIxQKeVZWVqzLkDigvr9IhJktdvfQsfbpYjGpkdT3Fzk5CgGpUdT3FykbhYDUCEVh59n/rOcP/1rF4YIibjizMz8d2Z2U+ur7i3wdhYDEvc+25HH3zKV8simPs7qnct/oPur7i5wkhYDErUNHC/njvz8n44McmjWow6T0QXyn/ymYWaxLE4kbCgGJS7NXbuc3r33G5r2HuWpYGr/6Rk995FOkHBQCEle278vnvlmf8ebSbZzauhEv//AMQp2ax7oskbilEJC4UBR2nvtwPQ+9vYqCojC//EYPbjqrC3Vq61M/IhWhEJBqb/mWfUx4dSmfbNzLWd1T+d2lfenYomGsyxKpERQCUm0dOlrIn/9vNU/Nz6ZZg2T+fOVARg9oq4VfkShSCEi19N7KHfz6tWVs3nuY9KEd+NWonjRtUCfWZYnUOAoBqVZ27MvnvlnLeWPpVrq3asRLPzyDIVr4Fak0CgGpFsJh57lFG3jorZUcKQpzx0WnMv7srlr4FalkCgGJuRVb93H3q0v5eMNezuzWggcu7UenVC38ilQFhYDEzOGjRfz53dU8NW8dTeon88crBnDpwHZa+BWpQgoBiYk5qyILv5v2HOaKUAfu+mZPmjXUwq9IVVMISJXasT+f385azj8/3UrXlg15cfzpDOvSItZliSQshYBUiXDY+XvmBia+tZIjhWFuv/BUxp/Thbq1k2JdmkhCUwhIpVu1bT8TZn7KRxv2MrxrCx4Y04/OWvgVqRYUAlJpDh8tYtLs1fz1/cjC7yPfH8CYQVr4FalOThgCZtYDeBrY4O5XBmMPAOcBBkxw9zlmlgw8BvQCHLjF3ZeZWRNgKtAGOAyMc/dNZtYWyAAaAjuBse6eF/UZSkzM/Xwnv3ltGRt2H+L7ofZM+GYvLfyKVEMncyXOMGBS8QMzOx8Y6O7DgcuAJ8ysNnANUOjuZwG3AlOCp9wBZAbjjwEPB+MTgYxgfC5wVxTmIzG2Y38+t/79Y67LWETtJOOF8afz0OUDFAAi1dQJzwTcfbqZnVtiaCTwUrBvi5mtB3oE438NxpeYWQszaxiMXx08dxZfBso5wLhgewbwOjChQrORmAmHnRcyNzLxrRXkF4T5+QWn8sNztfArUt2VZ00gFVhY4nEu0DIYz/26cXcPm1mSmdUCkt29sNSxx2Rm44HxAGlpaeUoWSrTqm37ufvVpSxev4czurTgd2P60lX3+BWJC+UJgT1ASonHKcHYicYPBOPhIAwKzMzc3Usce0zuPoWgvRQKhbwcNUslyC8oYvLs1Tw5dx2N69XmD98bwGWnaeFXJJ6U59u55gOjAcwslUgraFWp8R5AQbDQW3L8QmBJ8DqZwKhgewwwr3xTkFiYt3onF/3xfR57by2XDmrHu7efy+WD2ysAROJMec4E3gQuMrMFRELkNnfPN7OpwFNmNi8YHx8cPxGYZmbpQAFwczB+JzDVzCYAeXy5PiDVWO6BI9z/z+X8Y8kWuqQ25PmbhjG8a2qsyxKRcrJINyZ+hEIhz8rKinUZCSccdmZkbeR/3lrJ4aNF/Ojcrvzo3K7US9bCr0h1Z2aL3T10rH26WExOaPX2yMJvZs4ehnVuzgNj+tGtlRZ+RWoChYAcV35BEY+9t4Yn5q6lYd3aPHx5f/X9RWoYhYAc0/zVufz6taXk7DrEZae15+6Le9KiUd1YlyUiUaYQkK/YdeAIv3tjBa9+vJnOqQ15/sZhDO+mhV+RmkohIAC4Oy9lbeLBt1Zw8Eght47szi1a+BWp8RQCwpod+7n71WUsyt7N0M7NeXBMX7q1ahzrskSkCigEElh+QRF/eW8Nj89dS4M6tXnossjCb61aWvgVSRQKgQS1YE0u97y2jOzcg3x3UDvu/lYvUrXwK5JwFAIJZteBIzzw5gpmfrSZTi0a8OwNwxjRXQu/IolKIZAg3J2XFm/iwTcjC78/Pb8bPz6vmxZ+RRKcQiABrNlxgHteXcqH2bsZ0qkZD47pR/fWWvgVEYVAjZZfUMTjc9by+Jy11EuuxcTv9uP7oQ5a+BWRLygEaqD8giJmfrSZKe+vJWfXIS4d2JZ7vtWblo218CsiX6UQqEF27M/nbwvX89yHG9h98Ch92zVh+rihnH3qcW/aJiIJTiFQAyzfso+p87OZ9ckWCsJhLujVmhtHdGZo5+b6sjcR+VoKgTgVDjtzPt/B1PnZfLBmF/WTk0gf2oGxZ3amU2rDWJcnInFCIRBnDh8t4pWPNpHxQTbrdh6kTZN63PXNnqQPSSOlQXKsyxOROKMQiBM79uUzfeF6nv1wPXsPFdC/fQp/vnIgF/c7heSk8twqWkREIVDtfbYl74t+f2HYuah3a248qwuhjs3U7xeRClMIVEPhsDN7ZaTfv3DdLhrUSeLqYR0Ze2YnOrZQv19EokchUI0cOlrIKx9t5un52azLPUjblHrcfXFPrhiSRkp99ftFJPoqFAJmdj8wEmgA/AH4AFgArAoO2ezuV5tZMvAY0Atw4BZ3X2ZmTYCpQBvgMDDO3TdVpKZ4tC0vn+kLc3juww3kHS5gQPsUJqUP4pt926jfLyKVqtwhYGYXAQOAM4H6wEJgNfC8u99e6vBrgEJ3P8vMBgJTgOHAHUCmuz9kZpcADwPp5a0p3izb/GW/P+zON/q04YYRnRmsfr+IVJGKnAkMBGa7uwOHzCwLaA98x8xOB/YDE919DpGzhb8CuPsSM2thZg2D8auD15sFTDrWDzKz8cB4gLS0tAqUHHvhsPPuyh08NW8dH2bvpmGdJK49oxNjz+xEh+YNYl2eiCSYioTACuBmM5sMpALnA/9y91MBzKw38IaZDQ3255Z4bi7QsuS4u4fNLMnMarl7uOQPcvcpRM4eCIVCXoGaY+bQ0UJeXryJjPnZ5Ow6RLum9bnn4l5cMbQDTeqp3y8isVGREPgnMAyYC6wDlvHlWgDuvtzMPgK6A3uAlBLPTQnGiscPBOPh0gEQ77bmHeaZBet5/sP17MsvZGCHpjz6jR6M6tOG2ur3i0iMVSQEDPiNu7uZnQY8Ahw1s2R3LzCztkBvIuEwHxgNfGBmPYACd88zs+Lxx83sQmBJhWZTjXy6aS9T52fzxqdbCbszqm8bbhjRhcEdm8W6NBGRL1QkBFoDrwQLmLnA94mcGUw1swIiIXGzu+8zs6nAU2Y2D6hF0N8HJgLTzCwdKABurkA9MVcUdv5vxXamzstmUc5uGtWtzXXDO3H9cPX7RaR6ssi6bvwIhUKelZUV6zK+4uCRQl7K2sjTC3JYH/T7x57ZiSuGdKCx+v0iEmNmttjdQ8fap4vFKmDL3sM8syCH5xdtYH9+IaelNeVXo3pyUe/W6veLSFxQCJTDJxv38tT8bN5cuhUg6Pd35rQ09ftFJL4oBE5SUdj59/JtTJ2fTWbOHhrXrc24Mztx3fBOtG+mfr+IxCeFwAkcOFLIjMyNPL0gm427D9OheX3+69u9+f6QDjSqq78+EYlvehc7js17DzPtg2xeWLSR/UcKCXVsxj0X9+LC3m1IqqWvdBCRmkEhUMrHG/YwdX42by3bBsDF/U7hhhGdGdihaYwrExGJPoUAUFgU5p3l25k6P5vF6/fQuF5tbhzRmWuHd6Jd0/qxLk9EpNIkdAjszy/gxcyNTFuQw6Y9h0lr3oB7v9Oby0Pq94tIYkjId7qNuw/xzIIcXsjcyIEjhQzt1JzffLs3F/RqrX6/iCSUhAqBxev3kDE/m7eWbaWWGd/qH+n392+vfr+IJKaECIH9+QVcm7GIjzfspUm92ow/uyvXDe/IKSnq94tIYkuIEGhcL5mOzRtw6cB2XD64PQ3V7xcRARIkBAD+dOWgWJcgIlLt6FvOREQSmIJ0DBcAAAVVSURBVEJARCSBKQRERBKYQkBEJIEpBEREEphCQEQkgSkEREQSmEJARCSBmbvHuoYyMbOdwPpyPj0VyI1iOfFAc675Em2+oDmXVUd3b3msHXEXAhVhZlnuHop1HVVJc675Em2+oDlHk9pBIiIJTCEgIpLAEi0EpsS6gBjQnGu+RJsvaM5Rk1BrAiIi8lWJdiYgIiIlKARERBJY3IeAmTU0s8fMbK6ZZZrZg8H4A2a2wMwWmtm5JY7/hpltNrMflhgba2YrzGxO8OeXMZjKSYnGfIPxH5jZYjN738zur+JplEmU/o3fKvHvO8fM1sZgKictSnMeZmbzg9dYaGZnxWAqJy1Kc25nZm8E855nZh1iMJWTVpY5m1kXM5sZ/PebZWbfC8abmNlLwXzfMbP2ZSrC3eP6D9AWGBFs1wJWAVcBb5TYvxKoHTy+Dfgf4IclXuPnwHdiPZcqnO+5wCtA3eBx7VjPq7LnXOr1vglMjvW8quDf+UNgSLDdD/gk1vOqgjk/D1wWbJ8LvB7reUVrzsDpRC76AmgHrAy2fwvcGWxfAvy9LDXE/ZmAu29x9/nBw4bAUWAw8FLxfiJXGPcIHv8ZOFLqZZoCvwlS9zkz61wlxZdDlOb7E2Ax8LaZvQP0qoLSyy1Kcy7pTuDhSis4CqI0521ErjIl+N9tlVx2hURpzgOBd4Pt94EzKrnsCinLnN39P+5e/G0JbYHVwfZIYEawPQsYXpYa4j4EiplZEjAd+CXQiK9eXp0LHPOS6cB97j7U3c8AZvLlX2i1VcH59gTC7n4ecB/wdGXVGU0VnHPxa5wL5Lj7hsqoMdoqOOebgUfM7FPgyeBxtVfBOa8ARgXb6UByZdQYbWWZs5m1Af4E3BIMffF1Eu4eBpLM7KTf22tECJhZMvAs8KK7vw3sAVJKHJISjB1T8BdXvP0K0N7MrJLKrbCKzhcoCp6Pu38AnFKd5wtRmXOxCcDE6FcYfVGY8yvAWHfvD3wH+IeZ1a6seqMhCnP+BZBuZnOAU4DPK6nUqCnLnM3sFOAF4CZ33xjsL318uOR72onEfQiYWR0ifymvu/sLwfB8YHSwP5XI6eOqr3mNASW2LwA+86DBVt1EY77B8SOD4/sA26rrfCFqc8bMhgF57v61x1UHUZpzF6D4jWIbkd8mG1ZKwVEQpTlvdvdL3P1cIvPNqLyKK64scw4WfF8Gfuzuy0u8TMnjLwSWlKWGav1bwUm6kcgCUAszKz7dvR3YbmYLiATdbe6e/zWvMdrMngTygX3A2Eqst6KiMd9fA8+b2XigABhXifVGQzTmDHA3cG9lFRll0ZjzLcDrZrafyG+K97l7XiXWXFHRmPNYM7sWqAe85u5PVGbBUXDSczazR4A2wGMlTtxHEjmznWZm6UT+/1ymtp+uGBYRSWBx3w4SEZHyUwiIiCQwhYCISAJTCIiIJDCFgIhIAlMIiFSQmbUPLk4SiTs14ToBkSoRXG37KDAMaAbsBQ4AdYBDwTE/I/KFhDtLPf1md19cddWKnByFgMjJ+wGQ5O6Dgis9FwLjgd1Ervos9rC7PxqLAkXKSiEgcvKO1T79DpGrNEXikkJA5OT9DRhuZkuIfOXvk8A6vvy65mK/NLPrS43d7e7vVH6JImWjr40QqaDgi72eDb60rOR4jrt3iklRIidJnw4SKSMzW1hq6ADweixqEakonQmIlNHxfsM3s1eJfId9sUHAxyUev+Hu1fp+zpJ4tCYgUg5mllVq6JC7nx2TYkQqQGcCIiIJTGsCIiIJTCEgIpLAFAIiIglMISAiksAUAiIiCUwhICKSwBQCIiIJ7P8B1bMqv8XvDKYAAAAASUVORK5CYII=\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "df_last.groupby([\"연도\"])[\"평당분양가격\"].mean().plot()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "4tHcd_E7eMBu",
    "outputId": "12d0eba5-f1d7-4316-aadd-71e8261633f8"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a578b38>"
      ]
     },
     "execution_count": 44,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "df_last.pivot_table(index=\"월\",columns=\"연도\",values=\"평당분양가격\").plot.box()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "rCIniz7zeMBv",
    "outputId": "53700d23-cac8-4890-b8a2-a71775933de8"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a641ba8>"
      ]
     },
     "execution_count": 45,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1080x216 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#일부데이터에는 월데이터가 누락이 된 것 확인 \n",
    "\n",
    "p=df_last.pivot_table(index=\"연도\",columns=[\"월\"],values=\"평당분양가격\")\n",
    "p.plot(figsize=(15,3),rot=30)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "afXZNw2HeMBx"
   },
   "source": [
    "## seaborn 시각화"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "lB9tiar-eMBx"
   },
   "outputs": [],
   "source": [
    "import seaborn as sns\n",
    "\n",
    "#평균 구하는게 기본값\n",
    "\n",
    "#검정색 라인?\n",
    "#이상치를 제거한 신뢰구간 95% \n",
    "#sd는 실제 관측치에서의 표준편차를 보여준다\n",
    "#none은 아예 안보이게 할 수 있다"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "Uu4kaJYGeMBy",
    "outputId": "7c50867b-011a-44c3-e840-4118b4165ed0"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a718cf8>"
      ]
     },
     "execution_count": 47,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 720x216 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(10,3))\n",
    "sns.barplot(data=df_last,x=\"지역명\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "vDrGboMOeMB1",
    "outputId": "5b9e8317-3a0a-4f10-ba7c-b10316986491"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25a761ef0>"
      ]
     },
     "execution_count": 48,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "\n",
    "sns.barplot(data=df_last,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "woue52mTeMB4",
    "outputId": "8a025db1-b5e2-4e29-ce28-92cefeab2628"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<seaborn.axisgrid.FacetGrid at 0x1c25a62af28>"
      ]
     },
     "execution_count": 49,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1440x1800 with 17 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#서브플롯 구하기\n",
    "\n",
    "sns.catplot(data=df_last,x=\"연도\",y=\"평당분양가격\",kind=\"bar\",col=\"지역명\",col_wrap=4)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "dMXT9idteMB6",
    "outputId": "964a6f6f-9ba5-46d6-9fa4-ed86dd6b4ced"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.legend.Legend at 0x1c25c937f98>"
      ]
     },
     "execution_count": 50,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "iVBORw0KGgoAAAANSUhEUgAAArgAAAE9CAYAAADgVRHZAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjMsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+AADFEAAAgAElEQVR4nOzdeXxU5dk//s91ZiaTTFayQNgCGBEQbKBEbanWuoB9qhaLj3Wp+MOlWFHRLha1rbutQtWWqrSoLT5a69LWCli0PmL9qTx1QYiEJQiEJazZ98xyzvX945xJJiErzJCFz/v1opk558yZe9Dih3uu+7pFVUFERERENFAYvT0AIiIiIqJoYsAlIiIiogGFAZeIiIiIBhQGXCIiIiIaUBhwiYiIiGhAYcAlIiIiogHF3dsDOFYyMzN19OjRvT0MIiIioi6tXbu2TFWzunntYLfb/QyASTg+Ji8tAIWhUOj6qVOnHmrvguMm4I4ePRqffvppbw+DiIiIqEsisqu717rd7meys7MnZGVlVRqGMeA3OLAsS0pLS08+cODAMwC+3d41x0PKJyIiIhrIJmVlZdUcD+EWAAzD0KysrGrYM9btX3MMx0NERERE0WccL+E2zPm8HeZYBlwiIiIiiomcnJxJAPCjH/1o2IQJE06eOnXquOLiYg8AFBUVxU2bNu2kzl7/1FNPpf/oRz8a1tP3PW5qcImIiIgo+t577z3f/PnzcwDA7Xbrrl274svKygrC5//xj38kb9myJX7jxo2bduzY4Zk+ffpJqampIb/fb6SkpJiAHYBfffXV9PT09FAgEDD2798fl5ub21heXu6ZNWtWRU/HxBlcIiIiIjpiZ511VkNBQcGWgoKCLUuWLNl9yimn1EeeX7t2rW/GjBnVhmHgxBNPDKalpYVWrly5/fXXX98Wed3tt9++v6CgYMs//vGPbfn5+bVr164tuuuuu/YeyZgYcImIiIgoKhYtWjTk5ptvbtW6a8qUKY1vv/12qmVZKC4u9hQVFSXMnj171HXXXTeqo/t8/PHHyZMmTZpw//33jziScTDgEhEREdFRe+WVV1JWrVo1aO/evZ7I47NmzaoZM2aMf9KkSRMuuOCCE1999dVty5cv3/Hb3/52T/iazMzM4O9///vBeXl54//7v/879+KLL64oLCzcfKQzuKzBJSIiIqKjsmLFiuSHH354WGFhYeHMmTNzBw0aZM6ePbsqfP6JJ57YC6BVWM3NzQ08+OCDewHgrrvuKr3rrrtK2953ypQpjSNGjAj2dDwMuERERER0xH75y19mvfPOOylvvPHGtqFDh4ZWrVq1bfbs2aO+9a1v1Yav2bhxo/eyyy47IfJ1gUBAMjMzQ2vWrNkKAMFgELfeeuvw999/P8XtdmswGJSpU6fWLVmypKSnY4pZwBWRNABLAYwEIABeAfAagDUAipzL9qrq90TEA+BJABMAKIB5qlooIikAngWQDaARwLWqWiIiwwD8EUAigFIA16hqdaw+CxERERG17wc/+EF55OzrsGHDQu+88872yGsmTpzoLyws3Bx5rKioKO6aa64ZHX7+u9/9LrOystK9fv36zS6XC5Zl4aabbhr+4IMPDvnlL395oCdjimUNrhfAvar6VQBnALgRQCaAF1X1G86v7znXzgYQUtUzAcyHHYwB4CcAPnGOPwlgkXP8YQB/dI6/B+COGH4OIiIiImgoBKuqBmpavT2UPiU9PT0qvyHZ2dnB3bt3xxUVFcX5/X7ZsWOHp7i42Dt48OC+U6KgqgcBHHSeZgEIARgM4CIR+QqAWgAPq+q/AZwL4GnndetFJENEEp3j4RC8AsBi5/FZAK51Hr8CYDmAO2P1WYiIiOj4pYEgtLIGWlENtSy4TowHXHG9Pax+Yffu3YUdnRs3blwgXJ4AAFdeeWV1IBCQn/zkJyNKS0s96enpoYsuuqjq5ptvLu/p+8a8BldEHgYwF8ACAKtU9Q3n+MkA3hCR02DP7JZFvKwMdihuPq6qloi4RMQA4FHVUJtr23vvuc57IycnJ9ofjYiIiAYwbfLDqqiGVtdBDAF88ZBGf28Pa0CbM2dO1Zw5c6q6vrJzMW8Tpqp3wK7DvRpAfsTxTQA+AzAWQCWA1IiXpTrH2h63VNUCEBQRaXNte++9VFXzVTU/K6vdDExERETUijY2wdxzAOaOEqCuAZKYAPElQAx2V+0vYvZPSkTGiUg4VTYAqAbwVWdBGZyFYicDKATwAYBvh18HIOgsGos8Ph3Aeud+nwD4pvP4OwDej9XnICIiooFPVaH1jTB37YNVvBdo8kOSfJCEeLTMqVF/EcsSBT+A3zkh1wc7rO4A8J6IBGF3VrhBVWtE5FkAz4jI+7BD91znHg8DWCYiVwAIArjBOf5TAM+KyJ2wg3O4HpeIiIio29RSoKER1qEKwB8APG5IcmJvD4uOUiwXme0EcHk7p1a0c20jWhaTRR4vA3BhO8d3ADj76EdJRERExyO1LGhtPbS0EggEgfg4SJKvt4c14Gzfvt1zxRVXnPDxxx8X7du3z33DDTeM3LNnj9flcmkgEDDOO++86l//+tf7XC5XVN+XxSRERER03FDThFVZA2v7Hui+Q4DLgCQnQjyerl9MXXrkkUey7rjjjuz2zi1YsGDYl7/85Yb169dvWbt2bdGnn3665eOPP058+eWXU9u7/mhwJzMiIiIa8DQUglbVQcsrAUuBBC8k3tvbwxpwampqXIMHDw61d27atGl1zz//fOaYMWP8aWlpZnFxsbe0tNQzefLkxmiPgwGXiIiIBiwNBKFVtdDyKkDEDrbshhAz7733XvL5559fvXXr1rhZs2blBoNBSU1NNQHgxhtvrPjKV77S8O677ybt3LnTm52dHXz//feLhgwZYkZ7HAy4RERENOCoPwCtqIZVVdvSw/Y4CLbBl1aNtPaXRrWY2Bia1eC5/L/2dHXdhg0bvJZlydtvv516/fXXVxQWFm4O1+Dm5eWNbx5jMCi7du2KP/HEExuXLFkyGABOP/30uqVLl5ZEa8wMuERERDRgaKMfVnkltKYe4nbZPWzZ5ivmKisrjauvvnrMH/7wh11+v1+++c1vnviPf/xje/h8QUHBlg8//DBh69at8eXl5a4nnngi+7bbbjsIAOeee25tTk5Ou2UNR4oBl4iIiPo1VQUammCVVQL1jXarryTfcRlsuzPTGgsXX3zxCT/72c/2nXbaaY0AsHDhwpLf/va3Wbfccktp22szMjLMe+65Zy8APP/88xnx8fFWTk5OdTTHw4BLRERE/VJzD9vSSqCxCYjzsIdtL/nf//3fbZ6IThTnn39+3fnnn1+3ffv25oN/+tOfMj788MMUn8/XXHPr9/uNtLS0qNfgDvxiFCIiIhpQ1LJgVdfC2rEH1p4DgGXZrb68cb09tOOWpxtt1hoaGgzTbJ1lvV6vtX79+oRoj4czuERERNQvqGlCa+qhZZVA0AQS4iBebs7Ql+Xm5gY//vjjIgB48cUXdx+r92XAJSIioj7tsB628exhS51jwCUiIqI+qVUPWwBIiIe4WF1JXWPAJSIioj7leO1hS9HDgEtERER9gjb6YVVU2T1sDYM9bOmIMeASERFRr2nVw7ahEXC7GWzpqHG+n4iIiI45tRRa1wBr1z5Yu/YBwRAkKRES72W4HSB2797tPu2008YBwN/+9reUvLy88Xl5eeNfeumlVAB46623ki655JLRsXhvBlwiIiI6ZtSyYNXUwSousXvYmuxh298Fg0FceeWVOSeffPKEk08+ecKiRYsyI8/v37/fvXbtWt8FF1xQdcEFF1Rt2LAhoW0/3GhjwCUiIqKYU9OCVVkLa/seaMkhwBB7O924rjcIoL5tyZIlGZZlyaZNmzZ/9tlnW5577rmsTZs2Nf+Nxev1WmPHjvWPHTvWn5iYaK1atSrN5XLFdEyswSUiIqKY0ZAJramFllYBlsUetgOQZVmHHTNNs7nOJD093brmmmsq/X6/nH322WN/9atflcydO3fE6tWrU/Py8upjMSYGXCIiIoo6DQSh1bXQ8mpAlT1sj5Hgq78cqQeKo7q9m2SPafBceteejs7feOONFf/3f/+XNH78+JNVFXPmzCk95ZRT/Lt3727OmUVFRXFXX331aJ/PZz366KNDnn766d2XXHJJ1dKlSzM7uu/RYMAlIiKiqFF/AFpVA62oAQwBErzsYTvAeb1effnll3d1dP75559Pe+aZZzIfeuihveedd1793/72t5Sf/OQnw6+77rqyWI2JAZeIiIiOmjb5YZVXQ2vq7EDLVl+9orOZ1libPHny+PXr128JP09KSrK+9a1vVc2ePbtq9uzZVT/72c+yzzvvvPpLLrmk5pJLLqlZvXp1YlJSUkxWm/GvVERERHREVBXa0ARz935YxSVAQ6Pdw9YXz3B7HCotLW21YjA9Pd269957D4afL1u2LCvy/DnnnFP/3HPPxSSQcwaXiIiIekRVgfpGZ3OGJiDOA0lK7O1hUR8wadKkCZHP4+PjrU8//bQIABoaGoy250ePHu1fuXLljmiPgwGXiIiIukUtC1rXAC2tBPwBwBsHSWawJdvevXs3dHa+srKy4FiNhQGXiIiIOqWmBa2ph5ZVAEETiGewpb6NAZeIiIjaxR621F8x4BIREVErGgzZrb7KqwEoEM8ettS/MOASERERgDY9bAX25gzsYUv9EAMuERHRca5VD1uXsIct9XsMuERERMcpbWiCVV4Fra2HuF12D1sGWxoA+L0DERHRcURVofWNMHfug7VrL9AUgJGcCEng5gxd0aYArNKK3h5Gn2dZVvPjnJycSW3Pm6a9eVlRUVHctGnTTorFGDiDS0REdBxQS6F19a172HJzhg5pyISWVUIPlEEPlME6UAZU1gBuF1z5E8G/CrSWl5c33jRNMQxDt23blvDZZ59tzM3NDQDAX/7yl9SHHnpoGAC4XC7ds2ePt6KiIqY9cRlwiYiIBjA1LWhtPbSsEgiGuDlDO1QVqKqF5YRZPVAGLa0ATGcm0hcPyc6EMeEEIC0F0N4db19UUFCwBbBnZefMmTN6//797hdffHGQYRi44oorqq+44opqANi2bZvn6quvHhPr8TDgEhERDUB2D9s6e8Y23MPWG9fbw+oTtL7RnpU9GA605fasNgC43ZAhGTAmT4CRnQnJzgCSE5vLN7S+sU+3TCv5130jm8q2+6J5z/jM3IYRM+7Z09V1q1evTvzpT386YtmyZTsff/zxwZ9++mmiauu/DSxZsiTze9/7Xlk0x9ceBlwiIqIBRIMhaHUttKwK7GELaCAIPVTRUmpwsAyoqbdPikAy02CcNAqSnWn/Sk9la7Qe+vDDDxNuv/32EdnZ2cHXX399+/Dhw0PPPvvsHqB1De7HH3+c8Pbbb6euXbt2S6zHFLOAKyJpAJYCGAm7m94rqvqYiDwE4Gzn2J2q+m8R8QB4EsAE2BP/81S1UERSADwLIBtAI4BrVbVERIYB+COARAClAK5R1epYfRYiIqK+TgNBaGW108NWgATvcRfU1LKg5VUtZQYHyqHlVUB4FjElyZ6VnTwBkp0BGZwO8Xh6d9BR1p2Z1mjLz89vev3113dkZWWZbc9dd911hwDgX//6V+Itt9wyauXKlds8x+D3PJYzuF4A96rqJhFxA9gsIiUAJqvqNCekrhaRSQBmAwip6pkiMhl2MJ4G4CcAPlHVhSIyE8AiAFcAeBjAH1X1FRG5FcAdAO6M4WchIiLqk7TJD6uiGlp9fPWwVVWgpt6umw2XGhysAEIh+wJvnF03mzuyudRAfAm9O+gByuv1alZWlvnSSy+l/vrXv842TVNEBCkpKaFFixaVPPLII1lvvfVW6ltvvfXF6NGjg8diTDELuKp6EMBB52kWgBCA0wG86pzfJyK7AIwDcC6Ap53j60UkQ0QSnePfc+6xAsBi5/FZAK51Hr8CYDkYcImI6DiijU2wyo6fHrba5G+elQ2HWjQ02SddBmRwOoxTxkKyM2BkZwKpyQP696OvqaysNG6//faRH3300ZZhw4aFAGDNmjUJV1111QkFBQWbFyxYUHosxxPzGlwReRjAXAALAOQDiCwsLoMdfjO7Oq6qloi4RMQA4FHVUJtr23vvuc57IycnJ1ofiYiIqFeoKtDQBKu0EmhoBDweGAOwI4KGTGhpResWXVW1LRekp8IYPbylbjYzDeJy9d6ACfHx8WoYBj799NOE8847r87v98vHH3/sGzRoUCg+Pv6Y952IecBV1TtE5AEAbwIIAkiNOJ0KoNL51dnxOue45QTdoIiI2kvzwte2995LYZc7ID8/n009iIioX2q3h+0ACbaqClTWwNofUWoQ7vwA2CUX2ZkwJp5oh9khGewG0QclJCTo8uXLv1i0aNGQX/3qV0PdbrdOnjy54bXXXtvR0WvGjRsXWLNmzdZYjCeWi8zGAahQ1VIADQCqYZchXAngzyKSCbs8oQjABwC+DeBD53VBVa0WkfDxJSIyHcB65/afAPgmgFUAvgPg/Vh9DiIiot6iltPDtrQSCASB+P4fbLWuoXlW1q6bLbc/GwDEeewWXVNPdupmMyFJUe14RTGUl5fnf+GFF3b39jiA2M7g+gH8TkSyAPhgh9iVAM4VkTWwtwm+VVWbRORZAM+IyPvO8bnOPR4GsExEroA9+3uDc/ynAJ4VkTthB+dwPS4REVG/p5YFra5zNhsw7VZfyf1v1lIDQejB8laBFnUN9klDIJmDYIwfY8/QZmcCg1KOu84PFBuxXGS2E8Dl7Zya3861jWhZTBZ5vAzAhe0c3wG71RgREdGAoZYFram3g23ItFt9ueJ7e1jdoqYFLa+ENpcaOC26wlKTYQwfDMnOsmdmBw+CuNmOn2KD/2YRERH1suYa20MV9tf1CfGQeG9vD6tDqgpU19k7ge13Sg0OObPNgB3MszPhCm+gMCQDktA/gjoNDAy4REREvURV+0WNrTY22TOykaUGTX77pMsFGZIOI29cS4uulCS26DrOPPXUU+nbtm2Lf+yxx/aFjy1evDijpKQkbuHChfvbe81ll102avbs2RUXXnhhbXvnjwYDLhER0TGmqkB9I6zwAitvXJ9ZTKWhUOutbQ+UAdV1zeclIw1G7siWFl0Zacf1VsDUfZdeeunoyy+/vOKSSy6pifV7MeASEREdIy19bCvsTQriezfYqmVBK2rsmtlw7WxZJWA5nTWTfZAhmTC+dJJTN5sBiRtYW9tS9Lz44ouZ77zzTkr4eWVlpfvyyy8vDz//4osv4lNTUw/bzjcWGHCJiIiOAW1sgnWoAqhv7JU+tqoKtNeiKxje2tZjh9n8SXaLriEZfWZWmfqHs88+u3rOnDnNgXbVqlXNYfe1115L8fl81oIFC0a89dZb2zIzM00AuPnmm0ctX768aunSpSXRHAsDLhERUQxpox9WWSVQW2/3eT1GwVb9gcNbdNU32icNA5I1CMbEXDvUhlt0sW6239vw3n0j6yq2R/VvJknpuQ2nnHXPns6umT59el1CQoLu27eveYo/Ly+vcfLkyY1//OMfBz355JOD33zzzW3r1q2LP++888Y+/vjjuwHgiSee2MUaXCIion5CmyKCrTu2wVZNE1pa2dyeyzpQBlRUt1wwKAVGztCIrW0HQdzc2pai48orrxz1+eefdxiqt27dmlBWVrY+JSXFmjFjRn1+fv5Wd4xbxDHgEhERRZH6A7DKqqDVtRCPG0j0RXVmVFWBqtqIMoNwiy5na1tfvL1xgrOBggzJ6NMtxyi6upppjYUXX3xxV+TzMWPGTNy4ceMmn8+n4WOrV69OfPXVV9OWLFmyNz093QKAs846qzYnJycQizEx4BIREUWBBoLQ8ipYVbUQlwFJik6w1YbG5lnZcGcD+J1M4HbbW9tOHg8jOwuSnQEkJ7LUgPqchoYG49ChQ61WKM6bN68iVu/HgEtERHQUNBCEVlbDqqixg21iwlEFTFWF7i+F9flWWHsPATVOiy4RSGYajLGjIEOdUoP0VG5tS/3G6tWrUydNmjQh8ti8efMOxiLoMuASEREdAQ2FoJU10LIqwJCjD7YhE9bWnbDWb7G7G3g9MEYNg0weD8nOgAxOh3jYoov6vuLi4o1tj1144YW1lZWVBcdqDAy4REREPaAhE1pVY+8+JmLXvB7FLKrWN8L8vAjW51vt3rjpqXCdczqMCSew5yzREWLAJSIi6gY1TWh1LfRQJaB61MHWOlAGa/0WWEU7AcuCjBkO15QJkJyhrKElOkoMuERERJ1Q07KDbVklYFlAwpEHWzUtWNt2w1q3Gbq/FPC4YXzpJLgmj4cMSun6BkTULQy4RERE7VDLglbXQ0vL7RZcCfEQ1xEG28YmWBu+gFlQBNQ1AKnJcJ11qr3RgjcuyiMnIgZcIiKiCGoptLbO7i0bCjnB9sg2RbBKK2Gt3wxrczFgmpCcoXCd+xXI6GHsfkAUQwy4REREcIJtXb0dbAMhIMF7RBskqGVBd5TAXLcZWnIQcLtgnJwL15TxkIy0GIycqO8ZM2bMxOLi4o05OTmTdu/eXXis358Bl4iIjmuqCtQ3wjpYbm+gkOCFJHe462jH92nyw9q4Deb6Irt3bXIiXGd+GcaksdxJjAa0xYsXZzz44IPDBw8eHBw9erR/5cqVO9pe84tf/GLIa6+9lh557NChQ5777ruv5MYbb2QfXCIiomhQVaChyQ62TX4gPg6SnNjz+5RXwVy/BdamHUAoBBk+BK6vT4XkjmQZQh+kqnYXDPsJoADg/Gz3eOtr1DR7YdR931VXXVX22GOP7evo/AMPPHDwgQceOBh5bN68ecNTU1Nj8hvKgEtERMcdrW+EVVoJNDYBcZ4eB1tVhe7ca5ch7NoPuAwY48fAmDwBxuD0rm9wHDraYNl8TVvi/E/4vDgvkfBTaf1aEcAQIPyXD8Owj7kM+7WG/VPCxw3DuV4AGDDcBuBhfOrK/v37vZMmTZpQWlraYTPn8vJy9/Dhw4OxeH/+EyIiouOGNjbBOlQB1DfawTapZ6UIGgg6ZQhbgKpaIDEBrmmTYZxyEsQXH6NRH52BEizFJfbxcI9giXgu6OB45Dn78UDvMfzBmntHVlZt73mNTScGpeU2nDHt3j09ec3QoUP9hYWFm3NyciZ1dE1JSUncCSecEDj6ER6OAZeIiAY8bfLbM7a19Uc2Y1tVA3N9EayN24BAEDI0E8a0yTBOHHXErcM6fT9VIBC0uzi0zZddBcvDrj8GwbLT0Hl8BEuyBYNBlJWVtcqX06dPzz106FDzTO7mzZt9EyZMaACACy+88MQZM2ZUL1q0aH80x8GAS0REA5b6A7DKKqHVdRCPu0fBVlWhu/fDXLcFWlwCGAaMk0bBmDIBRnZmbMYbDAJ+5xvbxAQYWYNagmmHM5Ntz4HB8jjW05nWaHC5XPrSSy9lrFq1Ks3r9Vrz589vVWv79ttvb498Pnz48FMKCgq2xHJMDLhERDTgqD8Aq7wKWlULcbsgSb5uBz0NBmFtLrZ3G6uoBnzxME7/ElxfOqnHJQ3der+QCfj9UEshvnjI0CxIUgLEzf9EU/9w0003Vdx0002tOiE88MADw3prPAADLhERDSAaCEIrqmBV1kJcRs+CbU2dXYZQ+AXgD0AGp8M142swxo2GuI9so4cO38u0AL8fsBTwuCGD02Ek+rirGVGUMOASEVG/p8EQtKIaVkU1xCWQxIRuBVtVhe49ZHdD2G5/s2ucmANjynjIsMFR/XpfLcvusxsyAbcLMigVkpIIeONYRkADTnFx8UYAaG+Th717926I9fsz4BIRUb+loRC0sgZaVgUYPQi2IRNWkVOGUFoJxMfByJ9olyGkJEVvfOHFYoGQPb6UJEhqkr39r8FQSxQrDLhERNTvaMiEVtVCyyrtA774bm2qoHUNMAuKYG3YCjT6IRlpcJ33FRjjT4BEsbepBoJ2sAWAZJ+9KC0hPiYdF4jocAy4RETUb6hpQqtr7VlXS7sdbK39pbDWbYb1xS7AUkjuSLgmj4eMzI5aeYCGTKDJDwUgCfGQYWn2jDIXixEdc/x/HRER9XlqWtCaOmhpBWBa3ZoNVdOEtXUXrPVboAfKgDgPjMnj4cobD0lLjtq47MViFhAXBxmSASPJB4nrcPMmIjoGGHCJiKjPUsuC1tTbwTZkAgleiKvzjgZa3whrw1aYBVuBhkZgUApcZ58G4+TcqATP5sVipgW4DEhGmt0+jIvFiPoMBlwiIupz1FJobZ1dihAMAvHxkHhvp6+xDpbbZQhbdwKmBRk9HK4p4yGjhh118FRVewOGkLNYLDXZXowW7+ViMaI+iAGXiIj6DFWF1tZDD1XYnQcSvJ32hlXLgm7bbe82tu8Q4HHDmDTWrq9NTz368bRaLJYIIy2z23W/RMe7xYsXZ5SUlMQtXLgwqtvwdgcDLhER9TpVBeobYR0st7/+j/dCkjveNUwbm2Bt+AJmQRFQ1wCkJMF1Vj6MiSce9WYJGgoBTQF7sZgvHpKZBkn0RX2zB6KB4qOPPkqYO3fuqPDzvXv3ep977rlW2/M++eST6UuXLh0M2NtHl5aWek466aTGd999d1ssxsSAS0REvUZVgYYmWKUVQEMTEB8HSU7s8HqrrBLWui2wtuwAQiZkZDZc55wOGTP8qGZV1TTtYG0pEOeBZGfCSEzgYjGibjj99NMbCwoKtpSWlrqysrLMmTNnjsnKyjK3b2/JuOHtfIPBIH7zm99kLl++fNCf//znnbEaU8wCrogkAlgIYBIAH4C3ATwNYA2AIueyvar6PRHxAHgSwAQACmCeqhaKSAqAZwFkA2gEcK2qlojIMAB/BJAIoBTANapaHavPQkRE0acNTbAOVdgLwbwdB1u1LGhxiV2GsOcA4HLBmHACjCnjYWQOOvL3tyygKQCYph1qM9IgyYncLpf6tdc+uXfkwertHX/9cQSGpOY2fOfUe/d0dd3kyZNP3rt374Y9e/Z4x4wZE/jPf/7jW7ZsWda6det81113Xdnbb7+dsnXr1vipU6fWezwevf/++7PPOeecmlmzZtW4o9xOL5YzuKkA/qKqH4iIAWAzgBUAXlTVH7e5djaAkKWmHtwAACAASURBVKqeKSKTASwFMA3ATwB8oqoLRWQmgEUArgDwMIA/quorInIrgDsA3BnDz0JERFGijX57xrauwQ6WHQXbpgCsjdtgrt8C1NQByT64zvgyjEknQhLij+y9VVu2yzUMSFpSy2IxdkAgOiL/+te/EhsaGgy/328899xzaaeffnrtn/70p/S6ujpjzpw5pQsWLDj09NNPp8+fP/9QXl6eP/y6devWxf/nP//xRTvcAjEMuKq6D8A+52kigACAQQAuEpGvAKgF8LCq/hvAubBnd6Gq60Ukw5kBPhfA95x7rACw2Hl8FoBrncevAFgOBlwioj5Nm/ywSiuB2nrA00mwraiGuX4LrE3bgWAIMmwwXGdOhZw48ojKEJq3yw0GATGAlEQYqcn2AjYuFqMBpjszrbEgIli2bNmOxMREc+LEiU1paWnmhg0bEiorK12XXnrpmEOHDnleeOGFzPZeu23bNu+jjz4a1YVoMa/BFREXgP8BcDuAf6nqSc7xkwG8ISKnAcgEUBbxsjIAWZHHVdUSEZczG+xR1VCba9t777kA5gJATk5OtD8aERF1g/oDsMqqoNW1EI+73WCrqtCd+2Cu3wzduQ9wGTDGjYExeTyMIRlH9r7BEBAIQBWQxAT7Pr74LvvoElHPzJgxoz4YDOLWW28d/sEHHyS7XC6YpolTTz21/sknnyy59tprKyOvHzJkyJcOHjz4eSzHFNOA69TW/g+Al1X1zchzqrpJRD4DMBZAJeyShrBU51j4eJ1z3HKCblBERFU14trDqOpS2OUOyM/P1+h9MiIi6ooGgrDKq6BVtRCXAUnyHVYGoIEgrE3b7TKEyhrAlwDXVyfDOGUsJDGh5+8ZMgG/H6oKiY+HDMmCkZQA8XBNNVEs/e53v8usqKhwr1u3bovL5YJlWbj++utHPvLII1n33HPPoWM9nlguMosD8BcAf1XVl5xjEwBsU9Wgs1DsZACFAD4A8G0AH4rIOABBVa0WkfDxJSIyHcB65/afAPgmgFUAvgPg/Vh9DiIi6hkNBKGV1bDKqyEuFyQx4fBgW1ULs2ALrMJtQCBody34rzNgjB3V4xnW5sVilmmXPmSmw0j2cbEY0TE0ePDg0N69e+O2bdsWd8IJJwR27drl2bNnT9yUKVMaemM8sfwr7fUAvgEgQ0RucI69C+B8EQkCEAA3qGqNiDwL4BkReR+AAaesAPZismUicgWAIIDwfX4K4FkRuRNANVrqcYmIqJdoMAStrIGWV9m7fbWZsVVV6J4DMNdthu4oAQyBMXYUjCkTYAxtt9Ks4/dqu1hsUIpd+hDP7XKJesNVV11V1dDQIPPnzx9ZXl7uHjRoUOjb3/521S233FLe9tpYlycAgNjf8g98+fn5+umnn/b2MIiIBhwNmdCqGntbXUOc7WtbFm9pMARr8w5Y67fY4TfBC+NLJ8H1pXGQpO53M2peLBZwtstNSYKkJgEJ8dwulwYcEVmrqvndubagoGBnXl5eWddXDiwFBQWZeXl5o9s7x6IkIiI6Imqa0MpaaJmzDKLNFrZaUwezoAhW4RdAUwCSNQiuGdNgjBvTo13BNBgE/M52uc2LxRIgLnZAIKL2MeASEVGPqGlBq2uhpRWAqjODaodNVYXuPQRz/Rbott0AAMkdCdeUCZDhg7tdPmAvFgvYi8USvJBhWXYtbwz6ZRLRwMM/KYiIqFvUsqDV9dDScsC07GDrzKJqyIRVVGyXIRyqALxxMKaeDFfeOHsjhe7c37QAv9++tzcOMngQjKREbpdLRD3GgEtERJ1Sy4LW1tvBNWTaGyQ4nQ60rgHm51thfb4VaGyCpKfCde5XYEwYA/F0HUzVsuzFYqYFuAxIeqq9WMzLxWJE/dmYMWMmFhcXb8zJyZm0e/fuwshzpmnC5XKhqKgo7pprrhm9Zs2ardF+fwZcIiJql1oKrXOCbSBkB9t4LwDA2l8Ka/0WWFt3ApZCThgB1+TxkJyhXQbTlp3FIheLJTuL0xhqifqbxYsXZzz44IPDBw8eHBw9erR/5cqVOyLPf/LJJ/HXXHPNGAAwTVPq6+uNtqE32hhwiYioFVWF1jXYwdYfsINtsg9qmjC3FMNatxl6oAyI88DIGw/X5HGQtJSu7xsI2sEWAJJ9MLIzW5U5EFH/ddVVV5U99thj+9o7d+qppzYVFhZuBoCf//znQ1wuF+bMmTNyzZo1yZmZmaH2XnO0GHCJiAiAM7Na3wgrHGy9cZDkRGhDI8y1m2AWFAH1jUBaMlzfOBXGxBO7rI/VUAhoCkABiC8ekpkGSfT1qIsCEfU/+/fv906aNGlCaWlp8x8Sv/3tbzP+/ve/p994442H7rvvvoPhEoVYvH+HAVdEprVzeCOAieEnqromFoMiIqLYU0uBUMiufw2FYJVXAQ1NdrBN8sE6VA5z3RZYRcWAaUFGDYVr+lcho4d3Woagpt0BAZYFxMVBhmTa2+VysRhRzN1b8OjI7TU7u99guhtyU0Y33Jv34z09ec3QoUP9hYWFm3Nycia9+eabSYsWLRryta99ra6wsHDzTTfdNPyiiy4a8/DDD7c74xsNnc3gft/5+V8AVsDeMnc6gNcBrASgABhwiYj6KDUtwDTthWGm2dxPVgOh5m4FKoCE9/uJ8wCJCdDtexBatxm69xDgdsOYeKJdX5uR1vF7tV0slpFmb+LAxWJEx5VgMIiysrJW+dI0TSxevLhk4sSJfgBYsmTJ3u3bt3tCoVDM/nDoMOCq6jUAICL/p6rfF5FJqvq5iOwMnyMiot6hqnaYjAywgSDUH7AXhAWD9vlIIoDLAFwuO3gaBsL/ddEmP6yCIrsMobYeSEmC6+tTYUwcC4mP63gM/qD9Xi4XJC3Jbgnm5WIxot7S05nWaHC5XPrSSy9lrFq1Ks3r9Vrz588/GHn+ggsuqAOAWbNmjf773/++EwByc3ODu3bt8uTm5jbFYkydlSgIgF8DeMU59Gfn5/Gxty8RUS9SS+3w6gRYDZlAc4B1OhCoAoKWP5UNwwmwRnOAbb6fKtDQBK2qBWrr7bZftfXQmnr7eXkVEDIhI4bA9Y1TISeMaPX6VmNrtVgsEcbQzMN2MSOi48dNN91UcdNNN1VEHnvggQeGtb3uo48+So58PmrUqODzzz+/OxZj6mwGV0Xk2wBWi8gdqvpwLAZARHQ8UstyZl7t+lcNmkAg0BIegyF7YVY4wAqcAOuyf/riW331r8EgUNvQHFq1tr5VkEVt/eEzum43kJIISfbBmDTW/pU1qP3xBkP2zmJwFotlDYL4ErhYjIh6ZNKkSRMinycmJpofffTRMe+DW6GqN4jIlSIyU1VfB8DvnYiIuqDNpQN2GYH67eCqwYD9tX44bIo4M7HSMvvqdkO8cS3lA5YF1DdCq2taB9fw7GttA9Dkbz0AESAxAZKcCGNwBpCbA0lJtDdRSLZDLeK93VwspkCcB5KdCSORi8WIqGvFxcUbASCy3+3evXs3HKv37yrgGgCgqi+KyP2wF5i9FfNRERH1YXb9a5sAGy4fCNekWm2quQwBDFf75QP+gB1ca1rPuDY/rms4/H5eT3NYNYZmRQTXREhKIpDoO6L+smpZQFMAsEzA44FkDIIk+yDe9utwiYj6oq4C7osRj98VkVxV/XksB0RE1NsOr38NOfWv4fKBoP1VfWTmdBktJQQJLeUDappAXQO0yplpbaeEoLmeNcwQIMkOq8awIU4ZQevZ12gETrUsu5WXGfHTMCBpyfZisXh2QCCi/qnTgKuqj0c8Hayq78Z4PEREMdfcPiscYMP1peHuA+H618gXhbsPuAzAkwBDxJ7JbfJHlArUH15CUN94+AASvHZYTUuGMTK7JbiGSwiOcsGWqtqBNTK8hmeAnXFL+DN5PPZ4PB5IYoL9mIvFiKif68lOZj8G8HKsBkJEFC3N9a/N7bNCLR0Igt2vf9VQyF64VVMHrWtoVULQvHArZLZ+c5fLnnFN8sEYPaylbCA50Z4VTfJBPEe+iaSGw6pptgTYyM8Sfux22XWzCW67nMHtbgnoLpfd1outvIhogOqsTdgXaGk+IwBGiMjWiOeqqifFeHxERK20qn+NbJ8V7j4QCLa0zwLsP8UMaQl3Tv1reFvatjOukUEWje20Zwwv3MocBJwwApLk1LyGSwgSOl+41ennstSufTWdn1bL52guiQjPusZ77cVecW6Iy2UHWsNo/snSAiI6nnXWJmzssRwIERHQpn2WGVk+4ITXUET5QGT7rHD9q9M+SwPBzksH6hrsGdBIHrc9y5rsgzEk/fDSgSSfHSZ7+pnCmzJYTmmEpc70QUQfW4HdtsvjgcS77dnXuLazrgbLB4ioT6qtrTV+8IMfjNiwYYPP4/FoIBAwvvzlL9ctWbKkxOfztbuHwmWXXTZq9uzZFRdeeGFttMfT6fdkInINgAJV/Szab0x0LKilLV/btn9FlN+wz94surfr9Pe0m69vDrDh7WODzVu9tto+Nlw+EJ6djPNAVO2FW+Hg2qr7gH0c/kDr9xSxA2pyIoxhWS2LtZKTWmZfvZ4ez3yq2abWVa3m3+vmz+GUPiDOA/H6ALcH4nEdHl4560pE/dTChQuzPB6Pfv7551sAwLIsXH755aMef/zxrJ/97GeHAODSSy8dffnll1dccsklNbEeT1eFYPcCeF9ETgDwB1V9LtYDIuoODQcK02wOFho0gVDQWSjUwVal3dE2ZBxtmGt7u6jeLLpjO7pbHeHYpHX5AEQg/kD7s6/h0oH6xsPvHx9nh9SURBjDBzc/bu4+kJjQo9nPVrOu4X/ftE3JAODMurog8Ql2uUCcp1WpAFyuI2rXRUTUn5x++ukNr7/++qA//OEP6UOGDAnu37/fs3HjRt8NN9xQFr7miy++iE9NTTU7u0+0dBVwD6jqVSIyCMDDInIegKtVj/a/qkTt6zC4BgL2V9XBEBAK2bN8cAJG81e8ETN9xuG9RvuKgT5H1/zHgzqz5+Gv4sOPVYFGf5uNCuqcIGu30UIw1PqmLsNum5WSCCNnaMTsa0TrrB5sPnBYeyzLOvxvHiKAx5l19biBuLg2s65OeOWsKxERLrzwwtpx48bt+Oc//5m8fv16X0ZGRuiNN97YNnr06CAAvPbaayk+n89asGDBiLfeemtbZmamCQA333zzqOXLl1ctXbq0JJrj6Srg2mVuqpUAbhCRhwD8CsAd0RwEDXyHBVcz3Fs01ElwbbPCvU1w7ShWaDAIVNdCa+ph1Uc0yA8Hro4eh8NX8zH752GBrd3H4ddGPG73WPuv18PeOzIYRh5r857o6No255zXamf37+r1XX02RPzsKV+8HVbTUyGjhrXZcSvxsG1pO9LcHstsZ9ZVARWxyxtcBuD1AHFeu5+s221vORtRMsBZVyLqj+5ft3zk9ppDvmjeMzdlcMPdU769p6Pz06dPzz106FDzLMPmzZt9EyZMaHjmmWeyAGDr1q0JJ598csObb765bd26dfHnnXfe2Mcff3w3ADzxxBO7jnkNLoBDbZ7/HMAaERmuqnujPRjqf5r7iUYE2HaDq6VQaMvCIKDHwbX5PZsCsGrqgNo6+yvrmnpoTZ1Th1kHNPq7uMMRErGDkgiAiMfh4BU+D2nzuL3XHv56ae81bV/f/NrwcaPzsaH1exgiHV/bwWvafXzYZ2t9TDp9PewOAOEdt5IS7XDZhXY3JQjfM7I9lsdtLxYLdxjwOCUDrnDZANtjERFF09tvv729oKDA+9lnn/kA4Ic//OGo22677SAAnHbaaQ3vvPNO0pw5cypTUlKsGTNm1Ofn5291u4+8XWJ3dHX3pwFARGaq6uuqqiJyvqrGvDiYeleXwTVgN8OHqr2QBug4uDr73XcnUqgq0Nhkf3Vd4wRYJ8iGnx+265PbBaQk2V9fD8mwQ1OK3XNUEn32WMLjajeUdhLEIsMnxYSq2n1r292UIKLstc2mBIjzOLOuEYu0jqDDARHRQNLZTOux8vjjj+8CgDfffDNl//797rvuuqt09erVia+++mrakiVL9qanp1sAcNZZZ9Xm5OQEOr/bkemsD64LwAIArwNYICLL1VYjItmqeiAWA6LYaje4Ors3Nc+4dhRcDWkJrYbR/LVxT6KfWpbdezQ861pr/4x8fljjfK/HXumekgRjRLbz9XVSc4g90r6jfc1hpe2Rz7XNg1aXtj3WzjWH3fuwm3T//SKvExx2m07PSXPBdOtZ18hNCcI1r9yUgIio33j99ddTn3/++ayUlJTmRRSBQMA455xzagGgoaHBiCxjAIB58+ZVxGo8nc3gFgKAiGx2nm8UkdsBPAjAEhE3gG+q6v5YDY66T9vUt8KyOg+ukcEjCsG1ZRxmc5smO7jWtbRwqq4D6upbZufCEuLt0JqRBjlhRMuOT06Qlfi4no2hbb1ve3WhHQWz8IcOL1oDIqYQnQvabiLQXN8Zccy5tNVfELoizf9j/zNpPh4xsxx+3vZnc7loeLa6vetgdzpoLieIONf8fm3KDZpv6ZQzNE+Gt7l328ednQvfn5sSEBENGE1NTUYwGGz1h3lcXJy1adOm+PDz1atXp06aNGlC5DXz5s07GIugKz1piCAiD8Pui/sXEbkUwOmq+pNoDyoW8vPz9dNPP+3tYfSYNofWroPrYdoG1yj02dRQyA6sbWZdw89R13D4i5zeo3bpQJJdOhBeRJSSaH/d3NNxRIbYw7ZKtRcQSVycXR7hMrofvsLPIwNtxI8Or2/7OPL1Hd6r5RwDHhERRRKRtaqa351rCwoKdubl5ZV1feXAUlBQkJmXlze6vXOdlSgYAL4P4GQA/1bV1wBMBnC/c8lK5zz1UKuV3u0FV+cnQmYnwdUFuJxaV0/3Vph3a2zh/qM1dRGzsC3P0dBm61JDDm/flJrUMgubfGQ7PwHdDLEJPjvEetz2bKDHzTpMIiKi41xnJQpPAaiFXYN7mYhkA6gDkAqgAUCK85Mc7QbX8FajzV0F2guuTs2AhGdaI2oSozizp6pAk98uFaht6T7QMgvbzu5PLpdT65oIIys9YhbWCbA9bJ5/2Ji6E2J9iXaHBYZYIiIi6obOAu5UVT3VebxaRP4B4DUAj4jIIwB+AuCNWA+wv1BLYRWXtJQLNPdwRcyDa/MYVJ0FXHUdzMLW2y27IsV5nFKBJBjDBrcE15SkHvUf7XRcPQ2xTpBliCUiIqIj0VnAbRCRk1V1k4icBuCgqj4nIpkAFgF4V1WfPjbD7A8UCAQhSVHtrdz6HUwLqGtoCay1dRGzsPX2Aq62W9PGe+3Qmp4KGT3MXrQVMQsLb1xUwjZDLBEREfUVnQXceQCeFpEUADsAXAcAqvoogEePwdiOOxoyIxZstcy62n1g64C6xsNrchMTmvu/YmxOywKulKQeb1/a5fi6G2Lj4yBuhlgiIiLqHR0GXFXdCOBrkcdE5MdOwKUjoIFgS9usdmZhD1vAJWIv0kq2+78iovtAc4Dtxg5QPRpjeyE23FKLIZaIiIj6gc66KAyLeGo5GztcBmf2VkSuVNUXYzy+fkNVoU1+aH1ju5sXaE0d0NR2AZdhh9SUJBgnjGi1eYG9hanvqBZwdTjWLkOsF+KLZ4glIiKiI3baaaeN++tf/7r9jDPOGL979+7CY/nenZUovAzgFAAbAOQCGIbW3UBvA9BhwBWRRAALAUwC4APwtqreJSIPATjbudedqvpvEfEAeBLABNgxa56qFjrlEc8CyAbQCOBaVS1xwvcfASQCKAVwjapW9/jTR1Hw8eeh+w61Puhx2wu1UpNgZGe2bF4QXsCVmBCz/qcMsURERHSsjRo1atKuXbvaDbM///nPh6xYsWIQYPd/37dvX1x+fn7dP//5zx3RHkdnJQpnisj/hX+GD0dc0lUySwXwF1X9wOmpu1lECgFMVtVpTkhdLSKTAMwGEHLeazKApQCmwe7U8ImqLhSRmbAXt10B4GEAf1TVV0TkVgB3ALizx58+ilynnwJrfymMzEEtC7jiY7uFbI9CrMdjd3BgiCUiIqIY8Xq9VkfnHnzwwYM/+tGPSt94442U5cuXp9XX17seeeSRvbEYR2czuEBLoA3/PEVEtsLexrfTLdBUdR+Afc7TRAABAFMBvBo+LyK7AIwDcC6Ap53j60Ukw5kBPhfA95x7rACw2Hl8FoBrncevAFiO3g64X5sCKdoZ9S4Kdoh1djNjiCUiIqJOPLD2vZHbayujGkZykwc1/GLqWXu6um7Dhg3e6upq9xdffBH3ne98J7e4uLh5m96ysjLXvHnzRiQnJ1vTp0+vyc3NbbrtttsOPvHEE1mVlZWuF198cZfb3VUs7b6e3mkj7JlVAPigOy8QEReA/wFwO4DvAIjcSq4MQBaAzK6Oq6olIi5nNtijqqE217b33nMBzAWAnJyc7gy3V3QvxHoYYomIiKjPeu2111LT0tJCH374oa+wsHDzaaedNi587t///nfid7/73crw8z/84Q9D8vPzG6ZPn14DAP/5z398Z5xxRtQ2EOtskdnXACQ7PXATnMMKu/QgHUB8R6+NuIcHdrh9WVXfFJFvOK8PSwVQ6fzq7Hidc9xygm5QRERVNeLaw6jqUtjlDsjPz+90xjnWWoVY07R/JxliiYiIKIq6M9MaC+Xl5a4XXngh891339169tlnn/TVr361VVjdtGlTq9z4wx/+cH/kMb/f7z/jjDOiNp7OZnBvA7AF9szr5xHHvwvgmwB2dXZjEYkD8BcAf1XVl5zDH8Cut/2zs2HEOABFzvFvA/hQRMYBCKpqtYiEjy8RkekA1jv3+cQZwyrYs8Lvd+/jxpgCGgwyxBIREdFxwzRNfOtb38q955579g4fPjy0cOHCPXfffffQyGvuvvvuQzU1Ncbtt98+bP369T4AMAwDM2bMqL7nnnsOGlHuGtXZIrNLOzj+JOyOB125HsA3AGSIyA3OsR8DOCgiawAYAG5V1SYReRbAMyLyvnN8rnP9wwCWicgVAIIAwvf5KYBnReROANVoqcftRQIkxgMQJ8R67R27GGKJiIhoAHO5XPjzn/9cfOKJJwYB4OKLL669+OKLayNLFABg/vz5w4cMGRJcs2bNVpfLhcbGRvnud787+qmnnsq4+eaby6M5pi5rcEXkV6oaXsB1UXdvrKpPAXiqnVNr27m2ES2LySKPlwG4sJ3jO2C3GuszxBC4Rg3r+kIiIiKiASYcbjuTmZkZ2r17t7ekpMSTnZ0d2r59e1xZWZknKysr1NVre6qzGtxpsL9gnykiK5zDO51zXwVQpaqboz0gIiIiIur/Pv744yIACG/y8Mgjj+z/zW9+k3nDDTeMrK6udg8ePDg4f/78g5dddlnU9zLobAb3+87Pj5zHCuBVEbkEdt1rhojcoqr/f7QHRUREREQDi8vlwo9//OOyH//4x2VdX310OqvBvSb8WETGAzhHVVc5C7++AXuB2AIADLhERERE1Gd0umRNRJ5wHpYBON95bDo9aIsAjIjh2IiIiIiIeqyrngxTnZ+VALKdx+FZ3yzYHQyIiIiIiPqMbm3Vq6qmiISv3SAi98AuUVgZy8EREREREfVUVzO4g0XkahH5/wB4nGM/AmABeE9Vn43p6IiIiIioX7EsCwCwePHijJ/+9KdDAeC9997z5efnj5s6deq4adOmjd20aVMcAOTk5EyKxRi6msF9HsBo5/HvAUBVGwA8EIvBEBEREVH/smvXLs8FF1xwIgC4XC7dunVrwoEDBwoir7nllltyli1btvPLX/5y08svv5y6YMGC4StWrCiO1Zg664P7hfMwBHum1xCRiQCWAHgB9sKzy1Q1qjtPEBEREVH/MWrUqGBhYeFmAHjnnXcSf/3rXw9JTU21AGDZsmVZH3zwQbLH49Ha2loDAGpqagyPx6OxHFNnbcLGikgigB8CuADAPFVdJyKrAMwBMBl2ucLPYjlAIiIiIuqeBz5dO3JHTY0vmvc8ISWl4Rf5U/d0dd0LL7yQ9thjj2WvXLlyW/jYnDlzShcuXLj/k08+ib/11ltz6urqjMzMzNCzzz67K5pjbKurEoWrAPwv7B3MbhaR7wNIVdX1IrINwKuxHBwRERER9W2vvPJKykMPPTRsypQp9e++++7W8Oxt2N/+9reU7du3e2fOnFkZDAalvr7eePDBB7PPPPPM2liNqauAOwfANue6yQAyYS8wA4AgWhaeEREREVEv685Ma7Sdf/75dd/85je3pqSktAq255xzTl19fb2xc+fOuFAoBAB49NFHhz722GO7zzrrrLrJkyc33n333TEZU1cBF7AXlMUDuA2AFwBEZBCAU2CHXyIiIiI6ToVnbO+8887sFStWDHK73RoKhWTKlCn1S5Ys2XP66ac3FhcXe7Zu3er1+XzWNddcU3nqqaeOCwQCUlpaGpPJ0u4E3AzYATcBgAB4BMCnsGdyvx2LQRERERFR//HXv/415aOPPkpau3btFq/Xq5Zl4aabbhp+//33Zy9cuHB/QUFB/N///vdBr7322jYA+OSTT4oA4KWXXkqNxXi6E3D/G3YpwgkAoKorRORdAAFVDcRiUERERETUfwwePDhUWlrqKSws9E6cONG/Z88eT3Fxsfe8886rCV+zcuXKQZ999lli29eeeuqpDbm5ucFojqergPt7VX0OAETkSgD1AKCqddEcBBERERH1X1//+tcb7rvvvr333nvv0AMHDsQNGjQodOGFF1bNnz+/HAAuvvji2osvvrigq/tES6cBNxxunccvxn44RERERNQfzZo1q2bWrFk1XV8Ze11t1UtERERE1K8w4BIRERHRgMKAS0REREQDCgMuEREREQ0oDLhEREREdNRWrFiRnJeXNz4vL2/8mWeeOTby3Ny5c0c89dRT6ZHHZs6cOeatt95KisVYutMHl4iIiGjAUVVATahl/4JlQjUEtSyoFYKG/FArACsUBMwQLCsAKOAbOgmGJns0hQAAIABJREFU29vbw+9TFi9enPHCCy9ker1eBYBAICAXXXTRmBUrVhSHr/nlL385/KmnnhoSfl5SUuKdN29eaSzGw4BLRERE/Z6q5YTUkP3Tea5WCJYZhIYCUCsANYOwzCBgBuwQqwoRARRQACLq3FEg4gIMF0QMQFwwjDiEArWAWr35UfukG2+8sfz666+vaGxsNJ5//vm0V199Nf0Xv/jFgchr7r777pK5c+dWhp/PnDlzTKzGw4BLREREfcZhs6oRj1tmVZ2QGgrCsgJQMwBYChX7HuGMqgKIKiAuiGE0/xQxIB4fIIYdbntA0LPrj7WHPikaub26wRfNe+am+hp+duq4PR2dN00TCxYsGLZly5Z4wzBw9tln15x00klNv/jFL4aNGTPG/9RTT5WMGjUq8OSTTw558sknh0S+Ni0tzYzmWMMYcImIiCgmWs2qqmWXAETOqlrOzKoZaD2rCrWDZMSsqqpABG1mVQ0YRhzgjrefU69YunRpumVZ+PrXv15rGAZM05QJEyY0TZgwoam6utp19913DzEMAzNnzqxs+9o33ngjpaioyHv11VdXRXNMDLhERETUqchZVfur/1DrWVUz6ITUQMSsash+jXMPsZOqXRKANrOqYtgzq0c4q0otOptpjZUhQ4aEkpKSGsLP58+fP2rx4sW7AGDo0KHB7du3e2fMmFEDAAcOHPDccccdI5YtW9Zcm5uenh71WVwGXCIiouNI86yq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\n",
      "text/plain": [
       "<Figure size 720x360 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#지역별로 연도별 평당분양가격\n",
    "plt.figure(figsize=(10,5))\n",
    "sns.lineplot(data=df_last,x=\"연도\",y=\"평당분양가격\",hue=\"지역명\")\n",
    "plt.legend(bbox_to_anchor=(1.02,1),loc=2,borderaxespad=0.)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "VJhOrCHAeMB8",
    "outputId": "347dff16-b135-4207-e784-f82119d9c29a"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<seaborn.axisgrid.FacetGrid at 0x1c25adc7b70>"
      ]
     },
     "execution_count": 51,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1502.62x1800 with 17 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "sns.relplot(data=df_last,x=\"연도\",y=\"평당분양가격\",kind=\"line\",hue=\"지역명\",col=\"지역명\",col_wrap=4,ci=None)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "Dne3Kpd1eMB9",
    "outputId": "92cef94c-9517-440a-eff6-ac007013ed2c"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25b447978>"
      ]
     },
     "execution_count": 52,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#seaborn으로 box,violinplot 그리기\n",
    "#이상치 확인\n",
    "\n",
    "sns.boxplot(data=df_last,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "opER5720eMCA",
    "outputId": "5e12b8c9-9ffc-454f-de61-4bb863199164"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25b399828>"
      ]
     },
     "execution_count": 53,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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eOMNOnbsWOc+nnvuOf7617/y/vvv06yZ3joiIiIijaHoKYmqq6u58sor+eMf/0ifPn2orq5m/vz5rFixgsWLF7NlyxbOPfdcPv3000CgW11dTWZmJgcOHKB58+aMGDGC6urqsI+zZs0a/va3v7Fs2TKaNWvG7bffzosvvsitt95K165def/99+vtX2ZmZmD/5513Hq1atVLQLSIiIhKFeiMoY8yAOjavBo7zN6y1i+PRqXQxe/ZsevfuzT333MP27dsZMWIEW7du5fLLLwega9euHHnkkaxdu5bjjjuO4447jjZt2tC+fXs8Hg9dunTh1FNPpX379gwaNIitW7dy3XXXkZ2dze9+9zsqKipo27Ytbdq0AWDv3r20atWKnTt3kp+fT3V1NatXr2bgwIEAXH311YwZMwaA4cOH88033wBQU1PD1q1bueWWW9i1axe7du2ibdu2SXjFRERERFJXuKHLG3z/DwVmAoXAYOBt4J+ABRR4x+Czzz5jzZo1vPfee2RkZDBw4EBat25N//79A/fJy8sLBMBZWVksXryYnj17snbtWvr27cv06dMD992/fz+vvfYa27dv57rrruOQQw5h2rRptG/fnrvvvpsePXrQpk0bzj77bIYPH44xhq1bt5KRkcG3337LpZdeSrdu3bjooosAePbZZ5k8eTK33norf/rTnzj55JOD+iYiIiIikau3qom1dpS1dhTwf9baG4CN1tpVwCbfbdclrJdNVGZmJoWFhbRq1YqWLVsyaNAgvvjiC8rKygL3KSsro127dgBkZ2cD0KZNGzIyMjDGBO3vqKOOokOHDhx77LG88847/OMf/6Bly5asXr2aZ555ho0bN7JhwwZ69uzJvffeC0BGhvct0L59ey6//HJWrlwZ2F92djYtWrQgJyeHFi1aUFFREdfXQ0RERKQpqzfwNl6PA6/7Nk3z/W/j3qs0ceaZZ1JSUkJ1dTVVVVUsWrSIUaNGMWPGDAA8Hg9r166ld+/eMT3O559/Ttu2bcnNzQW8AfqaNWsoLS3l22+/BaCiooK3336bs846K7YnJSIiIiJ1qjfVxFprjTGFwPvGmLustY8ksF9J0alDp4gqkTRqf2H07duXwYMHk5+fT4sWLRg+fDhjx45l3LhxDBgwgJqaGp566qnASHe0LrzwQv7973/Tt29fcnJyAHj++ecpLy/n2muv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\n",
      "text/plain": [
       "<Figure size 864x216 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "plt.figure(figsize=(12,3))\n",
    "sns.boxplot(data=df_last,x=\"연도\",y=\"평당분양가격\",hue=\"전용면적\")\n",
    "\n",
    "#면적이 큰 분양가격이 편차가 있다. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "f6Pqqvg2eMCC",
    "outputId": "c247f8d1-8091-42d4-e6ef-6d7a5404ded0"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25e17f240>"
      ]
     },
     "execution_count": 54,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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8uNz/QzsEOTFCePbfEbP1igrK+O+cfdR6a8kcErgx1HlhyNgnGCgUhR/+vOfapdzTURTpkwhGAhwfgPP7QF81tc263E4t9V4vmXrVj777NCeSvFSXFxMWXkZWSm5UdtnprWvRJgYcs+ePdTU1JAewYjypqS7XZSVlce0DUsnjyiYN28eCxYswJd3HDh+PBOplI7UHDWMDz/8sM1GfUbbvHnzeP311zn9KB8jOtWd9sAhcNPgclRNFff/cVxC9p2vz+fzcf+f7mfXrl1m4ji0x2fDPBA4LUC5r5x77r0nIY917969zPvwQ0YqRVYzq6vqGwJ0FuG1KVMSpo0ntK5Kqrd+j4aW87qScTk9CTH5ZWjCxtQoJo9Ut3keiuVwAZ08Wmn9+vX84+mnMTKOwp93aGOev+vxqLROPPb44+2ux857773Hk088wZCOAa4dVNngazqnGNx5zEF27dzBHbffntBzQRmGwWOPPcZ3q78jeEIQIr2QTYfAqQEK9hYw7o/jEm4Q6LRp01CGIvLhcz9yIJyuFNt37EiYaUtCidrrSonqfpM8KQnRuyyUHJMamUE3YBgkJydzxRVXkJycTKCJxB5atjaWyVEnj1bYs2cP940bh9/hparfWSAN/DodTqr6nY0vKNz7h/sS4kqnKX6/n+eee46nn36aY7JruOfYMjyNVO0c3THAH449yN7d2/ndzTcl7Gjll156iS+++AJjmIHqcWhdsKwSKAVKwfGFw3xcXw4ETgqw7od1PPLoIwlzdb5//37mvP8+x9Lyu46QIZhtH69NmZIQAwerqqoAcDUxe26kXA53QlwAhBYda2z6db+huOSSS7jjjju45JJL8BuN/1281r5iuaCZTh4tVFRUxF13382B8koq+58P7sNfFSlvGpX9z6OoeD9333NPQjegFxQUcMfttzNz5kzO717NPcPK8TbVJgAM6RjgwRGluKr3c8cdtzN16tSEObGCOeHc1KlTMfoaqAENf/CkVBC/9VUoSOlhTsJdwTjWYNHCRbz66qsxjLr5pkyZgt/v54wo7MuJcIZhsGHjxoSobq1NHo7I53tqjFPctfuOp4qKClxOR6MrBrodwty5c3nuueeYO3cubkfjFwgua18VFRWNvq41dPJogeLiYu64804K9hZS2f98VEqHJn/GSMulsv95bN++gzvvujshE8iCBQu4/rpr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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#밀도추정그래프(연도별 평당분양가격 )\n",
    "\n",
    "sns.violinplot(data=df_last,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "FFoOZcxBeMCD",
    "outputId": "8e01ba48-dc8d-426f-9399-46e5a5538e50"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x1c25e26a550>"
      ]
     },
     "execution_count": 55,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# regplot-> scatterplot에 회귀선을 그려준다. 회귀선에 따라 데이터 상관관계 알 수 있다. \n",
    "# 양의 상관관계. 연도별로 약간의 양의 상관관계가 보임. \n",
    "# 그러나 hue 기능이 없어 색 구분 안된다\n",
    "\n",
    "sns.regplot(data=df_last,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "qW4KA493eMCG"
   },
   "outputs": [],
   "source": [
    "# 색구분 가능\n",
    "# 서브플롯 가능\n",
    "# 데이터몰려있으면 데이터 분포 확인하기 힘들다.\n",
    "\n",
    "sns.lmplot(data=df_last,x=\"연도\",y=\"평당분양가격\",hue=\"전용면적\",col=\"전용면적\",col_wrap=3)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "e61N92udeMCH"
   },
   "outputs": [],
   "source": [
    "#swarmplot은 범주형 데이터 산점도를 표현하기 적합\n",
    "plt.figure(figsize=(15,3))\n",
    "sns.swarmplot(data=df_last,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "QBjtbS1leMCJ"
   },
   "outputs": [],
   "source": [
    "#bins=n n개의 구간에 데이터를 나눠담겠다. 그리고 그 구간의 빈도수를 그림\n",
    "\n",
    "df_last[\"평당분양가격\"].hist()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "foX2DEq9eMCK"
   },
   "outputs": [],
   "source": [
    "#결측치 처리한 것 중, 평당분양가격 컬럼만 가지고 오기\n",
    "\n",
    "price=df_last.loc[df_last[\"평당분양가격\"].notnull(),\"평당분양가격\"]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "O7g6nVVMeMCL"
   },
   "outputs": [],
   "source": [
    "# 결측치가 없는 데이터만 사용 가능\n",
    "# kde=> 부드러운 곡선이 1이 되는 값이 y축\n",
    "\n",
    "sns.distplot(price)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "TVfH9gjyeMCP"
   },
   "outputs": [],
   "source": [
    "#빈도수 그리기.\n",
    "\n",
    "sns.distplot(price,hist=False,rug=True)\n",
    "sns.kdeplot(price)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "yIQesF2meMCQ",
    "outputId": "fc37c781-582d-4d47-a991-691aaf355c79"
   },
   "outputs": [
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 489.6x2080.8 with 17 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# 서울 그래프의 이상치가 매우 많다. \n",
    "\n",
    "g=sns.FacetGrid(df_last,row=\"지역명\",height=1.7,aspect=4,) \n",
    "g.map(sns.distplot,\"평당분양가격\",hist=False,rug=True);"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "M3eRau4leMCS",
    "outputId": "2cf7996a-30fe-4b46-fef5-f1a1fec56af9"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<seaborn.axisgrid.PairGrid at 0x1c9531fb780>"
      ]
     },
     "execution_count": 78,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 593.75x540 with 12 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light",
      "tags": []
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "df_last_notnull=df_last.loc[df_last[\"평당분양가격\"].notnull(),[\"연도\",\"월\",\"평당분양가격\",\"지역명\",\"전용면적\"]]\n",
    "sns.pairplot(df_last_notnull,hue=\"지역명\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "hwOaT3MheMCT"
   },
   "source": [
    "# 이상치 보기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "9YVd_2skeMCT"
   },
   "outputs": [],
   "source": [
    "# 3사분의와 최댓값의 차이/ 평균과 중위수의 차이 \n",
    "\n",
    "df_last[\"평당분양가격\"].describe()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "C7CLXc-seMCU"
   },
   "outputs": [],
   "source": [
    "max_price=df_last[\"평당분양가격\"].max()\n",
    "max_price"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "Ivu7cKYeeMCX"
   },
   "outputs": [],
   "source": [
    "df_last[df_last[\"평당분양가격\"] == max_price]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "mWku2UlUeMCY"
   },
   "source": [
    "# 2015년 8월 이전 데이터 보기"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "qT5MpnpAeMCY"
   },
   "source": [
    "## 연도와 월 분리"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "XitnMpROeMCY",
    "outputId": "8ebac93b-e4f6-42c9-a407-e77ec9e9aa10"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>연도</th>\n",
       "      <th>월</th>\n",
       "      <th>분양가격</th>\n",
       "      <th>평당분양가격</th>\n",
       "      <th>전용면적</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5841.0</td>\n",
       "      <td>19275.3</td>\n",
       "      <td>전체</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5652.0</td>\n",
       "      <td>18651.6</td>\n",
       "      <td>60㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5882.0</td>\n",
       "      <td>19410.6</td>\n",
       "      <td>60㎡~85㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5721.0</td>\n",
       "      <td>18879.3</td>\n",
       "      <td>85㎡~102㎡</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>서울</td>\n",
       "      <td>2015</td>\n",
       "      <td>10</td>\n",
       "      <td>5879.0</td>\n",
       "      <td>19400.7</td>\n",
       "      <td>102㎡~</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  지역명    연도   월    분양가격   평당분양가격      전용면적\n",
       "0  서울  2015  10  5841.0  19275.3        전체\n",
       "1  서울  2015  10  5652.0  18651.6       60㎡\n",
       "2  서울  2015  10  5882.0  19410.6   60㎡~85㎡\n",
       "3  서울  2015  10  5721.0  18879.3  85㎡~102㎡\n",
       "4  서울  2015  10  5879.0  19400.7     102㎡~"
      ]
     },
     "execution_count": 79,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_last.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "DirgAwq9eMCa",
    "outputId": "dde888b2-7cc3-4c72-bac8-cf9b20132b61"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역</th>\n",
       "      <th>2013년12월</th>\n",
       "      <th>2014년1월</th>\n",
       "      <th>2014년2월</th>\n",
       "      <th>2014년3월</th>\n",
       "      <th>2014년4월</th>\n",
       "      <th>2014년5월</th>\n",
       "      <th>2014년6월</th>\n",
       "      <th>2014년7월</th>\n",
       "      <th>2014년8월</th>\n",
       "      <th>...</th>\n",
       "      <th>2014년11월</th>\n",
       "      <th>2014년12월</th>\n",
       "      <th>2015년1월</th>\n",
       "      <th>2015년2월</th>\n",
       "      <th>2015년3월</th>\n",
       "      <th>2015년4월</th>\n",
       "      <th>2015년5월</th>\n",
       "      <th>2015년6월</th>\n",
       "      <th>2015년7월</th>\n",
       "      <th>2015년8월</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>18189</td>\n",
       "      <td>17925</td>\n",
       "      <td>17925</td>\n",
       "      <td>18016</td>\n",
       "      <td>18098</td>\n",
       "      <td>19446</td>\n",
       "      <td>18867</td>\n",
       "      <td>18742</td>\n",
       "      <td>19274</td>\n",
       "      <td>...</td>\n",
       "      <td>20242</td>\n",
       "      <td>20269</td>\n",
       "      <td>20670</td>\n",
       "      <td>20670</td>\n",
       "      <td>19415</td>\n",
       "      <td>18842</td>\n",
       "      <td>18367</td>\n",
       "      <td>18374</td>\n",
       "      <td>18152</td>\n",
       "      <td>18443</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>부산</td>\n",
       "      <td>8111</td>\n",
       "      <td>8111</td>\n",
       "      <td>9078</td>\n",
       "      <td>8965</td>\n",
       "      <td>9402</td>\n",
       "      <td>9501</td>\n",
       "      <td>9453</td>\n",
       "      <td>9457</td>\n",
       "      <td>9411</td>\n",
       "      <td>...</td>\n",
       "      <td>9208</td>\n",
       "      <td>9208</td>\n",
       "      <td>9204</td>\n",
       "      <td>9235</td>\n",
       "      <td>9279</td>\n",
       "      <td>9327</td>\n",
       "      <td>9345</td>\n",
       "      <td>9515</td>\n",
       "      <td>9559</td>\n",
       "      <td>9581</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>대구</td>\n",
       "      <td>8080</td>\n",
       "      <td>8080</td>\n",
       "      <td>8077</td>\n",
       "      <td>8101</td>\n",
       "      <td>8267</td>\n",
       "      <td>8274</td>\n",
       "      <td>8360</td>\n",
       "      <td>8360</td>\n",
       "      <td>8370</td>\n",
       "      <td>...</td>\n",
       "      <td>8439</td>\n",
       "      <td>8253</td>\n",
       "      <td>8327</td>\n",
       "      <td>8416</td>\n",
       "      <td>8441</td>\n",
       "      <td>8446</td>\n",
       "      <td>8568</td>\n",
       "      <td>8542</td>\n",
       "      <td>8542</td>\n",
       "      <td>8795</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>인천</td>\n",
       "      <td>10204</td>\n",
       "      <td>10204</td>\n",
       "      <td>10408</td>\n",
       "      <td>10408</td>\n",
       "      <td>10000</td>\n",
       "      <td>9844</td>\n",
       "      <td>10058</td>\n",
       "      <td>9974</td>\n",
       "      <td>9973</td>\n",
       "      <td>...</td>\n",
       "      <td>10020</td>\n",
       "      <td>10020</td>\n",
       "      <td>10017</td>\n",
       "      <td>9876</td>\n",
       "      <td>9876</td>\n",
       "      <td>9938</td>\n",
       "      <td>10551</td>\n",
       "      <td>10443</td>\n",
       "      <td>10443</td>\n",
       "      <td>10449</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>광주</td>\n",
       "      <td>6098</td>\n",
       "      <td>7326</td>\n",
       "      <td>7611</td>\n",
       "      <td>7346</td>\n",
       "      <td>7346</td>\n",
       "      <td>7523</td>\n",
       "      <td>7659</td>\n",
       "      <td>7612</td>\n",
       "      <td>7622</td>\n",
       "      <td>...</td>\n",
       "      <td>7752</td>\n",
       "      <td>7748</td>\n",
       "      <td>7752</td>\n",
       "      <td>7756</td>\n",
       "      <td>7861</td>\n",
       "      <td>7914</td>\n",
       "      <td>7877</td>\n",
       "      <td>7881</td>\n",
       "      <td>8089</td>\n",
       "      <td>8231</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>5 rows × 22 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   지역  2013년12월  2014년1월  2014년2월  2014년3월  2014년4월  2014년5월  2014년6월  \\\n",
       "0  서울     18189    17925    17925    18016    18098    19446    18867   \n",
       "1  부산      8111     8111     9078     8965     9402     9501     9453   \n",
       "2  대구      8080     8080     8077     8101     8267     8274     8360   \n",
       "3  인천     10204    10204    10408    10408    10000     9844    10058   \n",
       "4  광주      6098     7326     7611     7346     7346     7523     7659   \n",
       "\n",
       "   2014년7월  2014년8월  ...  2014년11월  2014년12월  2015년1월  2015년2월  2015년3월  \\\n",
       "0    18742    19274  ...     20242     20269    20670    20670    19415   \n",
       "1     9457     9411  ...      9208      9208     9204     9235     9279   \n",
       "2     8360     8370  ...      8439      8253     8327     8416     8441   \n",
       "3     9974     9973  ...     10020     10020    10017     9876     9876   \n",
       "4     7612     7622  ...      7752      7748     7752     7756     7861   \n",
       "\n",
       "   2015년4월  2015년5월  2015년6월  2015년7월  2015년8월  \n",
       "0    18842    18367    18374    18152    18443  \n",
       "1     9327     9345     9515     9559     9581  \n",
       "2     8446     8568     8542     8542     8795  \n",
       "3     9938    10551    10443    10443    10449  \n",
       "4     7914     7877     7881     8089     8231  \n",
       "\n",
       "[5 rows x 22 columns]"
      ]
     },
     "execution_count": 80,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_first.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "1EqlvpBzeMCb",
    "outputId": "e7506266-2337-4eb7-ef0b-64b677f9f043"
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 17 entries, 0 to 16\n",
      "Data columns (total 22 columns):\n",
      " #   Column    Non-Null Count  Dtype \n",
      "---  ------    --------------  ----- \n",
      " 0   지역        17 non-null     object\n",
      " 1   2013년12월  17 non-null     int64 \n",
      " 2   2014년1월   17 non-null     int64 \n",
      " 3   2014년2월   17 non-null     int64 \n",
      " 4   2014년3월   17 non-null     int64 \n",
      " 5   2014년4월   17 non-null     int64 \n",
      " 6   2014년5월   17 non-null     int64 \n",
      " 7   2014년6월   17 non-null     int64 \n",
      " 8   2014년7월   17 non-null     int64 \n",
      " 9   2014년8월   17 non-null     int64 \n",
      " 10  2014년9월   17 non-null     int64 \n",
      " 11  2014년10월  17 non-null     int64 \n",
      " 12  2014년11월  17 non-null     int64 \n",
      " 13  2014년12월  17 non-null     int64 \n",
      " 14  2015년1월   17 non-null     int64 \n",
      " 15  2015년2월   17 non-null     int64 \n",
      " 16  2015년3월   17 non-null     int64 \n",
      " 17  2015년4월   17 non-null     int64 \n",
      " 18  2015년5월   17 non-null     int64 \n",
      " 19  2015년6월   17 non-null     int64 \n",
      " 20  2015년7월   17 non-null     int64 \n",
      " 21  2015년8월   17 non-null     int64 \n",
      "dtypes: int64(21), object(1)\n",
      "memory usage: 3.0+ KB\n"
     ]
    }
   ],
   "source": [
    "pd.options.display.max_columns=25\n",
    "df_first.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "ec0-NLEleMCc",
    "outputId": "4f7a086f-18da-49cf-d764-34eacc30948d"
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "지역          0\n",
       "2013년12월    0\n",
       "2014년1월     0\n",
       "2014년2월     0\n",
       "2014년3월     0\n",
       "2014년4월     0\n",
       "2014년5월     0\n",
       "2014년6월     0\n",
       "2014년7월     0\n",
       "2014년8월     0\n",
       "2014년9월     0\n",
       "2014년10월    0\n",
       "2014년11월    0\n",
       "2014년12월    0\n",
       "2015년1월     0\n",
       "2015년2월     0\n",
       "2015년3월     0\n",
       "2015년4월     0\n",
       "2015년5월     0\n",
       "2015년6월     0\n",
       "2015년7월     0\n",
       "2015년8월     0\n",
       "dtype: int64"
      ]
     },
     "execution_count": 85,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#결측치 없음\n",
    "\n",
    "df_first.isnull().sum()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "MMNXXCKweMCe",
    "outputId": "ffc71ec0-2df2-4673-caae-57d82fa7a30f"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역</th>\n",
       "      <th>기간</th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>18189</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>부산</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>8111</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>대구</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>8080</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>인천</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>10204</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>광주</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>6098</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>352</th>\n",
       "      <td>전북</td>\n",
       "      <td>2015년8월</td>\n",
       "      <td>6580</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>353</th>\n",
       "      <td>전남</td>\n",
       "      <td>2015년8월</td>\n",
       "      <td>6289</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>354</th>\n",
       "      <td>경북</td>\n",
       "      <td>2015년8월</td>\n",
       "      <td>7037</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>355</th>\n",
       "      <td>경남</td>\n",
       "      <td>2015년8월</td>\n",
       "      <td>7665</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>356</th>\n",
       "      <td>제주</td>\n",
       "      <td>2015년8월</td>\n",
       "      <td>7343</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>357 rows × 3 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "     지역        기간  평당분양가격\n",
       "0    서울  2013년12월   18189\n",
       "1    부산  2013년12월    8111\n",
       "2    대구  2013년12월    8080\n",
       "3    인천  2013년12월   10204\n",
       "4    광주  2013년12월    6098\n",
       "..   ..       ...     ...\n",
       "352  전북   2015년8월    6580\n",
       "353  전남   2015년8월    6289\n",
       "354  경북   2015년8월    7037\n",
       "355  경남   2015년8월    7665\n",
       "356  제주   2015년8월    7343\n",
       "\n",
       "[357 rows x 3 columns]"
      ]
     },
     "execution_count": 86,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df_first_melt=df_first.melt(id_vars=\"지역\",var_name=\"기간\",value_name=\"평당분양가격\")\n",
    "df_first_melt"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "XPBANwyyeMCf",
    "outputId": "60c084d8-44d8-4e66-b969-4ea35caeb6e4"
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>지역명</th>\n",
       "      <th>기간</th>\n",
       "      <th>평당분양가격</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>서울</td>\n",
       "      <td>2013년12월</td>\n",
       "      <td>18189</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  지역명        기간  평당분양가격\n",
       "0  서울  2013년12월   18189"
      ]
     },
     "execution_count": 84,
     "metadata": {
      "tags": []
     },
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#컬러명 지역->지역명 으로 바꾸기\n",
    "\n",
    "df_first_melt.columns=[\"지역명\",\"기간\",\"평당분양가격\"]\n",
    "df_first_melt.head(1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "j7StbYPXeMCh"
   },
   "outputs": [],
   "source": [
    "# 연도와 월 분리하기\n",
    "\n",
    "date=\"2013년12월\"\n",
    "date"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "LPWoHiS_eMCi"
   },
   "outputs": [],
   "source": [
    "# split을 통해 '년'을 기준으로 텍스트 분리\n",
    "\n",
    "date.split(\"년\")[0]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "wab7L1E8eMCj"
   },
   "outputs": [],
   "source": [
    "#replace를 통해 월 제거\n",
    "\n",
    "date.split(\"년\")[-1].replace(\"월\",\"\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "DqITObaMeMCk"
   },
   "outputs": [],
   "source": [
    "#새로운 함수 만들기\n",
    "\n",
    "def parse_year(date):\n",
    "    year= date.split(\"년\")[0]\n",
    "    year=int(year)\n",
    "    return year\n",
    "\n",
    "y=parse_year(date)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "88lEHCuueMCl"
   },
   "outputs": [],
   "source": [
    "def parse_month(date):\n",
    "    month=date.split(\"년\")[-1].replace(\"월\",\"\")\n",
    "    month=int(month)\n",
    "    return month\n",
    "\n",
    "parse_month(date)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "n9WRMGkUeMCo"
   },
   "outputs": [],
   "source": [
    "#apply를 활용해 연도만 추출해서 새로운 컬럼에 담기\n",
    "\n",
    "df_first_melt[\"연도\"]=df_first_melt[\"기간\"].apply(parse_year)\n",
    "df_first_melt.head(1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "TlIZSR1beMCp"
   },
   "outputs": [],
   "source": [
    "df_first_melt[\"월\"]=df_first_melt[\"기간\"].apply(parse_month)\n",
    "df_first_melt.head(1)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "EwUGb5S9eMCq"
   },
   "outputs": [],
   "source": [
    "df_last"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "T5fyeWu2eMCs"
   },
   "outputs": [],
   "source": [
    "df_last.columns.to_list()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "YbbSQo4xeMCt"
   },
   "outputs": [],
   "source": [
    "#분석에 사용할 컬럼만 추출\n",
    "\n",
    "cols=['지역명', '연도', '월', '평당분양가격']"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "-UJx6pzPeMCv"
   },
   "outputs": [],
   "source": [
    "# df_last와 병합을 하기 위해서는 컬럼의 이름이 같아야 한다. \n",
    "# 이전 데이터에는 전용면적이 없기 때문에 '전체'만 사용\n",
    "# loc을 사용해서 전체에 해당하는 면적만 copy로 복사\n",
    "\n",
    "df_last_prepare=df_last.loc[df_last[\"전용면적\"] ==\"전체\",cols].copy()\n",
    "df_last_prepare"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "d1a4TnYleMCw"
   },
   "outputs": [],
   "source": [
    "df_first_prepare=df_first_melt[cols].copy()\n",
    "df_first_prepare"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "2csM5FMyeMCx"
   },
   "source": [
    "## concat으로 두 개의 데이터프레임 합치기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "8Z8OS3jieMCx"
   },
   "outputs": [],
   "source": [
    "# df_first_prepare 와 df_last_prepare 합쳐주기\n",
    "\n",
    "df=pd.concat([df_first_prepare,df_last_prepare])\n",
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "ZuCA1NvceMCy"
   },
   "outputs": [],
   "source": [
    "df[\"연도\"].value_counts(sort=False)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "U4zZXdIUeMCz"
   },
   "source": [
    "## pivot table로 분석하기"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "8ITPfnAneMC0"
   },
   "outputs": [],
   "source": [
    "#melt로 녹인 데이터를 다시 컬럼으로 만들기\n",
    "\n",
    "t= pd.pivot_table(df, index=\"연도\", columns=\"지역명\",values=\"평당분양가격\").round()\n",
    "t"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "VlUw2aVKeMC1"
   },
   "outputs": [],
   "source": [
    "# 위에서 그린 피봇테이블을 히트맵으로 표현\n",
    "# cmap -> 색상 지정\n",
    "# vmax,vmin -> 색상 지정 범위\n",
    "# fmt=\".0f\" -> 소숫점 단위 없이 표현\n",
    "\n",
    "plt.figure(figsize=(15,7))\n",
    "sns.heatmap(t.T,cmap=\"Blues\", annot=True, fmt=\".0f\") \n",
    "\n",
    "# 서울을 해가 갈수록 높아지고, 경기도와 부산은 최근에 많이 올랐다. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "92WRytKweMC2"
   },
   "outputs": [],
   "source": [
    "t.T"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "colab_type": "text",
    "id": "hIrRmyWCeMC3"
   },
   "source": [
    "# 통합데이터 시각화"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "pV7j0H08eMC3"
   },
   "outputs": [],
   "source": [
    "# 평당분양가격이 지속적으로 상승세\n",
    "\n",
    "sns.barplot(data=df,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "uPXahOkFeMC5"
   },
   "outputs": [],
   "source": [
    "plt.figure(figsize=(12,4))\n",
    "sns.pointplot(data=df,x=\"연도\",y=\"평당분양가격\",hue=\"지역명\")\n",
    "plt.legend(bbox_to_anchor=(1.02,1),loc=2,borderaxespad=0.)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "VAH5bGCoeMC8"
   },
   "outputs": [],
   "source": [
    "#서울만 barplot\n",
    "\n",
    "df_seoul=df[df[\"지역명\"]==\"서울\"]\n",
    "print(df_seoul.shape)\n",
    "\n",
    "sns.barplot(data=df_seoul,x=\"연도\",y=\"평당분양가격\",color=\"b\")\n",
    "sns.pointplot(data=df_seoul,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "kca-D9j5eMC9"
   },
   "outputs": [],
   "source": [
    "# 연도별 평당분양가격 violinplot\n",
    "plt.figure(figsize=(10,4))\n",
    "sns.violinplot(data=df,x=\"연도\",y=\"평당분양가격\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "oemPGH6leMC_"
   },
   "outputs": [],
   "source": [
    "#서울의 분양가격이 이상치로 보일 정도로 높다\n",
    "#2013년 데이터 양 자체가 적다.\n",
    "\n",
    "plt.figure(figsize=(12,5))\n",
    "sns.swarmplot(data=df,x=\"연도\",y=\"평당분양가격\",hue=\"지역명\")\n",
    "plt.legend(bbox_to_anchor=(1.02,1),loc=2,borderaxespad=0.)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "02Wl9l09eMDA"
   },
   "outputs": [],
   "source": [
    "plt.figure(figsize=(12,5))\n",
    "sns.swarmplot(data=df,x=\"연도\",y=\"평당분양가격\",hue=\"지역명\")\n",
    "sns.violinplot(data=df,x=\"연도\",y=\"평당분양가격\")\n",
    "plt.legend(bbox_to_anchor=(1.02,1),loc=2,borderaxespad=0.)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "_5XfiVbqeMDB",
    "outputId": "747d407f-0e4e-4152-e876-f82fba3a2f0e",
    "scrolled": true
   },
   "outputs": [
    {
     "ename": "FileNotFoundError",
     "evalue": "[Errno 2] File C:\\jupyter notebook\\data\\집값부동산 뉴스데이터_20130101-20161231 does not exist: 'C:\\\\jupyter notebook\\\\data\\\\집값부동산 뉴스데이터_20130101-20161231'",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mFileNotFoundError\u001b[0m                         Traceback (most recent call last)",
      "\u001b[1;32m<ipython-input-6-f4af88f46334>\u001b[0m in \u001b[0;36m<module>\u001b[1;34m\u001b[0m\n\u001b[0;32m      2\u001b[0m \u001b[1;31m# 한글 때문에 인코딩이 꺠져서, 인코딩 다시 설정(utf-8 or cp949)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m      3\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m----> 4\u001b[1;33m \u001b[0mdata\u001b[0m\u001b[1;33m=\u001b[0m\u001b[0mpd\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mread_csv\u001b[0m\u001b[1;33m(\u001b[0m\u001b[1;34m\"C:\\jupyter notebook\\data\\집값부동산 뉴스데이터_20130101-20161231\"\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\io\\parsers.py\u001b[0m in \u001b[0;36mparser_f\u001b[1;34m(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, skipfooter, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, cache_dates, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, doublequote, escapechar, comment, encoding, dialect, error_bad_lines, warn_bad_lines, delim_whitespace, low_memory, memory_map, float_precision)\u001b[0m\n\u001b[0;32m    674\u001b[0m         )\n\u001b[0;32m    675\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 676\u001b[1;33m         \u001b[1;32mreturn\u001b[0m \u001b[0m_read\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mfilepath_or_buffer\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mkwds\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    677\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    678\u001b[0m     \u001b[0mparser_f\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m__name__\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mname\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\io\\parsers.py\u001b[0m in \u001b[0;36m_read\u001b[1;34m(filepath_or_buffer, kwds)\u001b[0m\n\u001b[0;32m    446\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    447\u001b[0m     \u001b[1;31m# Create the parser.\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 448\u001b[1;33m     \u001b[0mparser\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mTextFileReader\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mfp_or_buf\u001b[0m\u001b[1;33m,\u001b[0m \u001b[1;33m**\u001b[0m\u001b[0mkwds\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    449\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    450\u001b[0m     \u001b[1;32mif\u001b[0m \u001b[0mchunksize\u001b[0m \u001b[1;32mor\u001b[0m \u001b[0miterator\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\io\\parsers.py\u001b[0m in \u001b[0;36m__init__\u001b[1;34m(self, f, engine, **kwds)\u001b[0m\n\u001b[0;32m    878\u001b[0m             \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0moptions\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;34m\"has_index_names\"\u001b[0m\u001b[1;33m]\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mkwds\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;34m\"has_index_names\"\u001b[0m\u001b[1;33m]\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    879\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m--> 880\u001b[1;33m         \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_make_engine\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mengine\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m    881\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m    882\u001b[0m     \u001b[1;32mdef\u001b[0m \u001b[0mclose\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\io\\parsers.py\u001b[0m in \u001b[0;36m_make_engine\u001b[1;34m(self, engine)\u001b[0m\n\u001b[0;32m   1112\u001b[0m     \u001b[1;32mdef\u001b[0m \u001b[0m_make_engine\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m,\u001b[0m \u001b[0mengine\u001b[0m\u001b[1;33m=\u001b[0m\u001b[1;34m\"c\"\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1113\u001b[0m         \u001b[1;32mif\u001b[0m \u001b[0mengine\u001b[0m \u001b[1;33m==\u001b[0m \u001b[1;34m\"c\"\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m-> 1114\u001b[1;33m             \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_engine\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mCParserWrapper\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mf\u001b[0m\u001b[1;33m,\u001b[0m \u001b[1;33m**\u001b[0m\u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0moptions\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m   1115\u001b[0m         \u001b[1;32melse\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1116\u001b[0m             \u001b[1;32mif\u001b[0m \u001b[0mengine\u001b[0m \u001b[1;33m==\u001b[0m \u001b[1;34m\"python\"\u001b[0m\u001b[1;33m:\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mC:\\anaconda\\envs\\song\\lib\\site-packages\\pandas\\io\\parsers.py\u001b[0m in \u001b[0;36m__init__\u001b[1;34m(self, src, **kwds)\u001b[0m\n\u001b[0;32m   1889\u001b[0m         \u001b[0mkwds\u001b[0m\u001b[1;33m[\u001b[0m\u001b[1;34m\"usecols\"\u001b[0m\u001b[1;33m]\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0musecols\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1890\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n\u001b[1;32m-> 1891\u001b[1;33m         \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_reader\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mparsers\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0mTextReader\u001b[0m\u001b[1;33m(\u001b[0m\u001b[0msrc\u001b[0m\u001b[1;33m,\u001b[0m \u001b[1;33m**\u001b[0m\u001b[0mkwds\u001b[0m\u001b[1;33m)\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0m\u001b[0;32m   1892\u001b[0m         \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0munnamed_cols\u001b[0m \u001b[1;33m=\u001b[0m \u001b[0mself\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0m_reader\u001b[0m\u001b[1;33m.\u001b[0m\u001b[0munnamed_cols\u001b[0m\u001b[1;33m\u001b[0m\u001b[1;33m\u001b[0m\u001b[0m\n\u001b[0;32m   1893\u001b[0m \u001b[1;33m\u001b[0m\u001b[0m\n",
      "\u001b[1;32mpandas\\_libs\\parsers.pyx\u001b[0m in \u001b[0;36mpandas._libs.parsers.TextReader.__cinit__\u001b[1;34m()\u001b[0m\n",
      "\u001b[1;32mpandas\\_libs\\parsers.pyx\u001b[0m in \u001b[0;36mpandas._libs.parsers.TextReader._setup_parser_source\u001b[1;34m()\u001b[0m\n",
      "\u001b[1;31mFileNotFoundError\u001b[0m: [Errno 2] File C:\\jupyter notebook\\data\\집값부동산 뉴스데이터_20130101-20161231 does not exist: 'C:\\\\jupyter notebook\\\\data\\\\집값부동산 뉴스데이터_20130101-20161231'"
     ]
    }
   ],
   "source": [
    "# 데이터 로드\n",
    "# 한글 때문에 인코딩이 꺠져서, 인코딩 다시 설정(utf-8 or cp949)\n",
    "\n",
    "data=pd.read_csv(\"C:\\jupyter notebook\\data\\집값부동산 뉴스데이터_20130101-20161231\")"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "UolXCb9keMDC"
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "z1hjy3xveMDD"
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "a5cObJ61eMDE"
   },
   "outputs": [],
   "source": []
  },
  {
   "cell_type": "code",
   "execution_count": 0,
   "metadata": {
    "colab": {},
    "colab_type": "code",
    "id": "2RByDx3geMDF"
   },
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "colab": {
   "name": "공공데이터분석1_전국 신규 민간 아파트 분양가격 동향.ipynb",
   "provenance": []
  },
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.6.10"
  },
  "toc": {
   "base_numbering": 1,
   "nav_menu": {},
   "number_sections": true,
   "sideBar": true,
   "skip_h1_title": false,
   "title_cell": "Table of Contents",
   "title_sidebar": "Contents",
   "toc_cell": false,
   "toc_position": {
    "height": "calc(100% - 180px)",
    "left": "10px",
    "top": "150px",
    "width": "165px"
   },
   "toc_section_display": true,
   "toc_window_display": true
  }
 },
 "nbformat": 4,
 "nbformat_minor": 0
}
