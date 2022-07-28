### state만 정의

- const [state] = useRecoilState(초기값);

### setState만 정의

- setState만 사용할 경우, 쉼표를 넣어줘야 한다.
- const [, setState] = useRecoilState(초기값);
