1. yoonho 사용자가 실행시킨 프로세스정보를 출력하는 명령어는? 출력형식은 환경변수도 함께 출력
ps -u yoonho e

2. yoonho 사용자가 실행시킨 프로세스를 강제종료 시키는 명령어는?
killall -9 -u yoonho
pkill -9 -u yoonho

3. PID가 1222인 프로세스의 NI값을 최대값으로 설정하여 우선순위를 최대한 높이는 명령어
renice -20 1222

