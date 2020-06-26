# Slide puzzle analysis
# 슬라이드 퍼즐 분석

This git has made for Slide Puzzle analysis which is from mobile game 'Last Origin'.\
이 깃은 모바일 게임 '라스트 오리진'의 슬라이드 퍼즐 분석을 위해 만들어졌습니다.

There're 4 ipynb file, 4 csv files, 1 zip file, 1 md file in this repository on 2020-06-26.\
이 저장소에는 2020-06-25 기준으로 4개의 ipynb 파일과 4개의 csv, 1개의 zip 파일, 1개의 md 파일이 있습니다.

>1. How_many_samples_will_I_need.ipynb
>2. Last_Origin_Slide_Puzzle_Analysis.ipynb
>3. Pattern_probability_that_already_seen.ipynb
>4. Possible_case.csv
>5. README.md
>6. Result_DB.csv
>7. Sample_Data_Extractor.ipynb
>8. sample_template.zip
>9. samples (80 hand typed).csv
>10. samples.csv

## How_many_samples_will_I_need.ipynb
This ipynb file is written in python 3.\
When expected random pattern pool is given, this code finds required samples amoount that unexpected-unseen-pattern existance probability goes to below 0.1%\
Basically it calculates (random_pool/(random_poo1+1))^samples <= (0.1/100) when random_pool is given and samples are increasing.

이 ipynb 파일은 파이썬 3 로 작성되었습니다.\
랜덤 패턴 풀이 주어졌을 때 예상치 못 한 패턴이 있을 가능성이 0.1% 아래가 되기 위해서 필요한 샘플의 개수를 찾습니다./
기본적으로 (랜덤풀/(랜덤풀+1))^샘플수 <= (0.1/100) 연산을 랜덤풀을 고정시키고 샘플수를 늘려가며 계산합니다.

## Last_Origin_Slide_Puzzle_Analysis_with_analysis_final_loading_version.ipynb
This ipynb file is written in python 3.\
It contains n by m slide puzzle simulator which is using A* algorithm to seek every possible puzzle states and save result as csv files\
Result is saved in to two files, 'Possible_case.csv' and 'Result_DB.csv'.\
Once simulation or loading from csv files is done, it start analysis by using data retrieved from 'samples.csv' file

이 ipynb 파일은 파이썬 3 로 작성되었습니다.\
A* 알고리즘을 통해 n x m 사이즈의 슬라이드 퍼즐의 모든 가능한 상태를 탐색하고 그 결과를 csv 파일로 저장하는 코드입니다.\
결과는 Possible_case_csv와 Result_DB.csv 두 개의 파일로 저장됩니다.\
시뮬레이션 혹은 csv 파일의 로딩이 완료되면 'samples.csv' 파일의 데이터를 불러와서 분석을 시작합니다.

## Pattern_probability_that_already_seen.ipynb
This ipynb file is written in python 3.\
Get sample from random pool 80 times while random pool is increasing.
Try 100 time for each case and take average and plot graph.
When 80 Last Origin Slide Puzzle samples were given, 48 patterns were observed so find pattern pool's size when 48 values are observable.

이 ipynb 파일은 파이썬 3 로 작성되었습니다.\
랜덤 풀로부터 80회 샘플을 얻으며 랜덤 풀을 증가시킵니다.
상황별로 100회 연산을 수행하고 평균을 취해 그래프를 그립니다.
80개의 라스트 오리진 슬라이드 퍼즐이 주어졌을 때 48개의 패턴을 관측했기 때문에 48개의 값을 관측가능한 패턴 풀의 크기를 찾습니다.

## Possible_case.csv
This csv file contains every possible cases of 3x3 Slide puzzle.\
Single unit data has form of [[7,8,9],[4,5,6],[B,2,3]].

이 csv 파일은 3x3 슬라이드 퍼즐에서 가능한 모든 경우의 수에 대한 데이터를 담고 있습니다.\
하나의 단위 데이터는 [[7,8,9],[4,5,6],[B,2,3]] 의 형태를 가지고 있습니다.

## README.md
This file is read.md.

이 파일입니다.

## Result_DB.csv
This csv file contains every possible cases of 3x3 Slide puzzle but unlike 'Possible_case.csv', it also contains movement data and indexs of mother-state.\
Single unit data has form of [[[7,8,9],[4,5,6],[B,2,3]],M]. (M is the mother-state-index)/
Unit datas are stored in list which every elements in list had same amount of movement./
[Unit data with 1 move 1, Unit data with 1 move 2, ...],[Unit data with 2 move 1, Unit data with 2 move 2, ...],...

이 csv 파일은 3x3 슬라이드 퍼즐에서 가능한 모든 퍼즐의 상태를 저장하지만 'Possible_case.csv' 파일과는 달리 이동 횟수와 이전 상태의 퍼즐의 인덱스의 정보도 포함하고 있습니다.
하나의 단위 데이터는 [[[7,8,9],[4,5,6],[B,2,3]],M] 의 형태를 가지고 있습니다. (M은 이전 상태 인덱스)\
단위 데이터들은 같은 이동횟수를 가진 단위 데이터들과 같이 리스트에 저장되어 있습니다.\
[1회 이동한 단위 데이터 1, 1회 이동한 단위 데이터 2, ...],[2회 이동한 단위 데이터 1, 2회 이동한 단위 데이터 2 ...],...

## Sample_Data_Extractor.ipynb
This ipynb file is written in python 3.\
Calculate similarity of current frame and past frame and by taking frame which similarity is in certain range, extract frame that have slide puzzle.\
Find position of each pieces by using template image from puzzle part, and make them as form of 789456B23 and save them with puzzle number as csv file.\

이 ipynb 파일은 파이썬 3로 작성되었습니다.\
이전 프레임과 현재 프레임 사이의 유사도를 측정하여 특정 구간의 유사도를 가진 값만을 얻는 방법으로 영상에서 슬라이드 퍼즐이 있는 프레임만을 얻어내는 코드입니다.\
이후 퍼즐 부분에서 추출한 퍼즐 조각의 템플릿 이미지로 퍼즐의 위치를 읽어서 이를 789456B23 형식으로 퍼즐 번호와 함께 csv 파일로 저장합니다.\

## sample_template.zip
This zip files has template images for Last Origin slide puzzle pieces.\
This folder should be located at py file's (or ipynb file's) directory.

이 zip 파일은 라스트 오리진 슬라이드 퍼즐들의 템플릿 이미지입니다.
이 폴더는 py 파일 (또는 ipynb 파일)의 주소에 위치해야 합니다.

## samples (80 hand typed).csv
This csv file contains 80 'Last Origin' in-game slide puzzle datas as sample.\
It has puzzle number column, and shuffled puzzle state column.\
Shuffled puzzle has str type and saved as form of 789456B23.\
On 2020-06-16, Last Origin slide puzzle has 6 types of puzzle and each type of puzzle has puzzle numbers 1 to 6.

이 csv 파일은 라스트 오리진의 인게임 슬라이드 퍼즐의 80가지 데이터를 가진 샘플 파일입니다.\
퍼즐 번호 한 열, 섞인 퍼즐 상태 한 열의 데이터로 이루어져 있습니다.\
섞은 퍼즐들은 str 타입으로 저장되어 있으며 789456B23 과 같은 형태로 이루어져 있습니다.\
2020-06-25 기준으로 라스트 오리진 슬라이드 퍼즐은 6가지 타입이 있고 이들은 1부터 6까지의 번호가 주어져 있습니다.\

## samples.csv
This csv file contains 500 'Last Origin' in-game slide puzzle datas as sample.\
It has puzzle number column, and shuffled puzzle state column.\
Shuffled puzzle has str type and saved as form of 789456B23.\
On 2020-06-16, Last Origin slide puzzle has 6 types of puzzle and each type of puzzle has puzzle numbers 1 to 6.\
This csv file is created by Sample_Data_Extractor.ipynb using [sample_vid](https://drive.google.com/file/d/1_Ij4yl3bBk1n4VoDmNJtzdYHjtHYMIdD/view?usp=sharing).

이 csv 파일은 라스트 오리진의 인게임 슬라이드 퍼즐의 500가지 데이터를 가진 샘플 파일입니다.\
퍼즐 번호 한 열, 섞인 퍼즐 상태 한 열의 데이터로 이루어져 있습니다.\
섞은 퍼즐들은 str 타입으로 저장되어 있으며 789456B23 과 같은 형태로 이루어져 있습니다.\
2020-06-25 기준으로 라스트 오리진 슬라이드 퍼즐은 6가지 타입이 있고 이들은 1부터 6까지의 번호가 주어져 있습니다.
이 csv 파일은 Sample_Data_Extractor.ipynb 를 통해 만들어 졌으며 [sample_vid](https://drive.google.com/file/d/1_Ij4yl3bBk1n4VoDmNJtzdYHjtHYMIdD/view?usp=sharing) 파일을 이용했습니다.
