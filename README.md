# 📱 Echo Messenger (C# Windows Forms 실습)

본 프로젝트는 C# WinForms를 활용하여 기본적인 UI 구성과 데이터 연동, 그리고 사용자 편의성(UX)을 고려한 이벤트 처리 로직을 학습하기 위한 실습 과제입니다.

---

## 📅 프로젝트 진행 단계

### [과제 1] 기본 UI 구성 및 데이터 연동
사용자가 텍스트를 입력하고 버튼을 눌러 목록에 추가하는 핵심 기능을 구현했습니다.

* **컨트롤 배치 및 속성 정의**
    * `Label`: 프로그램 제목 표시 및 폰트 설정 (에코 메신저)
    * `TextBox`: 사용자 메시지 입력을 위한 필드 (`textBox1`)
    * `Button`: 데이터 전송을 위한 실행 버튼 (`button1`)
    * `ListBox`: 전송된 메시지가 누적되어 표시되는 대화창 (`listBox1`)
* **데이터 연동 로직**
    * `button1_Click` 이벤트를 통해 `textBox1.Text` 값을 `listBox1.Items.Add()` 메서드로 전달하여 화면에 출력.
<img width="792" height="477" alt="111111111111111111" src="https://github.com/user-attachments/assets/f6a7b284-f23d-4e59-b314-2b531b53366f" />

---

### [과제 2] 사용자 편의성(UX) 강화
실제 메신저 사용 환경과 유사한 최적의 조작감을 제공하기 위해 메서드와 조건문을 활용한 편의 기능을 구현했습니다.

#### 1. 입력창 자동 정리 및 포커스 제어
* **기능**: 메시지 전송 작업이 끝나는 즉시 `textBox1.Clear()`를 호출하여 기존 입력을 삭제합니다.
* **효과**: 사용자가 다음 메시지를 입력하기 위해 기존 텍스트를 일일이 지워야 하는 번거로움을 제거했습니다.
* **포커스 유지**: `textBox1.Focus()` 메서드를 호출하여 전송 후에도 마우스 클릭 없이 키보드 입력을 즉시 이어갈 수 있도록 설계했습니다.

#### 2. 키보드 인터페이스 최적화 (엔터 키 전송)
* **기능**: Form의 `AcceptButton` 속성을 전송 버튼(`button1`)으로 지정했습니다.
* **효과**: 마우스로 버튼을 클릭하지 않고 키보드의 **Enter 키**만으로 메시지를 즉시 전송할 수 있어 실질적인 채팅 환경을 완성했습니다.

#### 3. 무의미한 데이터 입력 방어 (Exception Handling)
* **기능**: `string.IsNullOrWhiteSpace()` 메서드를 활용한 예외 처리 로직을 적용했습니다.
* **상세 로직**:
    * 내용이 아예 없는 빈 문자열 입력 차단.
    * 스페이스바만 입력된 공백(Space) 메시지 전송 차단.
* **효과**: 대화창에 무의미한 빈 줄이 추가되는 것을 방지하여 데이터의 무결성을 유지했습니다.
<img width="786" height="477" alt="22222222222222222" src="https://github.com/user-attachments/assets/eb07e7a2-75de-4a9b-9d09-7ffdae91632f" />

---<img width="786" height="478" alt="3333333333333" src="https://github.com/user-attachments/assets/89840fec-e954-48d2-8651-e0d06346d369" />


## 💻 주요 소스 코드 (Core Logic)

```csharp
private void button1_Click(object sender, EventArgs e)
{
    // 입력 방어: 내용이 실질적으로 존재할 때만 로직 수행
    if (!string.IsNullOrWhiteSpace(textBox1.Text))
    {
        // 리스트박스에 데이터 추가
        listBox1.Items.Add(textBox1.Text);

        // 입력창 정리 및 다음 입력을 위한 포커스 이동
        textBox1.Clear();
        textBox1.Focus();
    }
}
---<img width="616" height="272" alt="4444444444" src="https://github.com/user-attachments/assets/0c082ce3-4ce5-4f83-a6c7-9b7b6cffe8c1" />
<img width="616" height="272" alt="4444444444" src="https://github.com/user-attachments/assets/2ea3035a-ed5e-414d-8bd8-3121add885b6" />



## 🚀 향후 발전 방향 (Future Work)
현재 구현된 '에코 메신저'를 기반으로 향후 다음과 같은 기능을 추가하여 확장할 계획입니다.
1. **시간 표시 기능**: 메시지 전송 시 현재 시간을 함께 출력하여 가독성 증대.
2. **리스트박스 초기화**: 전체 대화 내용을 한 번에 삭제하는 'Clear All' 버튼 구현.
3. **색상 커스터마이징**: 사용자 취향에 맞게 배경색 및 글자 크기를 조절하는 설정 기능 추가.
