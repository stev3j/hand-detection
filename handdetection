import cv2
import mediapipe as mp

cap = cv2.VideoCapture(0)

mpHands = mp.solutions.hands
hands = mpHands.Hands()
mpDraw = mp.solutions.drawing_utils

while True:
    ret, frame = cap.read()
    imgRGB = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB) #표현할 이미지의 색
    results = hands.process(imgRGB) #이미지 전처리
    print(results.multi_hand_landmarks)

    #인식이 됐다면
    if results.multi_hand_landmarks:
        for handLms in results.multi_hand_landmarks: #각 점의 xyz좌표
            mpDraw.draw_landmarks(frame, handLms, mpHands.HAND_CONNECTIONS) #각 점 찍어주기


    #읽어온 프레임 출력
    cv2.imshow('frame', frame)
    #나가기
    if cv2.waitKey(20) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows() 