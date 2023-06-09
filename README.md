# 0609TIL 

## numpy

```(1)벡터생성```

1.np.array(리스트)

    - 직접 지정한 리스트 값으로 ndarray 생성
    - 자동으로 저장된 값으로 데이터 타입인 dtype이 정해진다.
      정수형의 기본은 int32(4byte)
      실수형의 기본은 float64(8byte)

2.랜덤함수 이용

    가. np.random.seed(1234) #랜덤값 고정
    나. np.random.random([갯수]) : 0.0 <= 값 < 1.0 사이의 임의의 float 값 반환, 갯수 생략하면 1 개 반환
    다. np.random.rand([갯수]) :  0 ~ 1의 균등분포에서 표본 추출, 갯수 생략하면 1 개 반환
    라. np.random.randn([갯수]) :  표준편차가 1이고 평균값이 0인 정규분포에서 표본 추출. 갯수 생략하면  1개반환
                            * 편차: 값- 평균값, 편차의 합은 0
    마. np.random.randint(최소범위, 최대범위, n개) : 주어진 최소(inclusive) ~ 최대(exclusive) 범위안에서 임의의 정수 n개 반환
        np.random.randint(최대범위, size=n개) :   0 ~ 최대(exclusive) 범위안에서 임의의 정수 n개 반환

3.특정값으로 설정

    가.  np.zeros(shape) : shape만큼  0.0 으로 채움. 기본 type은 float64
                        만약 정수형으로 저장하기 위해서는 dtype=np.int32 지정한다.
    나.  np.ones(shape) : shape만큼  1.0 으로 채움. 기본 type은 float64
                        만약 정수형으로 저장하기 위해서는 dtype=np.int32 지정한다.

    다.  np.empty(shape) : 초기화하지 않았기 때문에 임의의(arbitrary) 값으로 채움.

         Returns
        -------
        out : ndarray
            Array of uninitialized (arbitrary) data of the given shape, dtype, and
            order.  Object arrays will be initialized to None.
            
    라. np.full(shape, 값) : shape만큼 지정된 값으로 채움

4.arange

    4. np.arange([start,] stop[, step] 함수
     ==> 파이썬의  range 함수와 동일한 기능 제공, 단, 지정된 값의 타입에 따라서 반환됨.

    가. 변수 = np.arrange(n)		#  [0,n) 범위의 정수 , 만약 n값이 실수이면 실수값 반환됨.
	나. 변수 = np.arrange(n,m)	#  [n,m) 범위의 정수
	다. 변수 = np.arrange(n, dtype=np.float32)   #  [0,n) 범위의 실수
        변수 = np.arrange( n실수값 )   #  [0, n) 범위의 실수

5.linspace

     ==> 지정된 범위에서 균일한 간격으로 값을 반환
     np.linspace(start, stop, [num=50, endpoint=True])
     => [start,stop] 범위사이의 값을 num개 생성, 기본 type은 float64, num 값을 지정하지 않으면 기본은 50
     => 기본적으로 stop값이 범위에 포함됨.  interval [`start`, `stop`].
        포함시키지 않을려면  endpoint=False 로 지정한다. Default is True.

```벡터삭제```

1. ndarray 삭제


       문법:                      색인
         arr = np.delete(arr, idx|fancy|slice, axis )
       - 순방향, 역방향 모두가능
       - 삭제된 새로운 배열을 반환 (in-place가 False), 원본이 유지됨
       - axis=None 이면 flatten 적용됨. ==> 다차원이 1차원으로 만들어짐
       - slice인 경우에는  np.s_[::2]  형식 사용한다.
      
2. 값으로 삭제

        - np.where( (arr==5) | (arr==8)) 활용하여 일치하는 인덱스를 먼저 찾고 삭제한다.
        - np.delete(arr, np.where())

```벡터 추가 및 삽입```

 1. ndarray 추가

        문법:
        arr = np.append(arr, values, axis=None)
        - 추가된 새로운 배열을 반환
        - axis=None 이면 flatten 된후에 추가된다.

 2. ndarray 삽입
 
        문법:                        색인
         arr = np.insert(arr, idx|fancy|slice, value,  axis ).
         - fancy 사용시 value와 shape가 일치해야 된다.