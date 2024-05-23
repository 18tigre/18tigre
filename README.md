Public Class FormCalculadora
    Dim firstNumber As Decimal
    Dim secondNumber As Decimal
    Dim operation As String

    Private Sub FormCalculadora_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        Me.Text = "Calculadora Básica"
        txtDisplay.ReadOnly = True
        txtDisplay.TextAlign = HorizontalAlignment.Right
        txtDisplay.Font = New Font("Microsoft Sans Serif", 20)
    End Sub

    Private Sub btnNumber_Click(sender As Object, e As EventArgs) Handles btn0.Click, btn1.Click, btn2.Click, btn3.Click, btn4.Click, btn5.Click, btn6.Click, btn7.Click, btn8.Click, btn9.Click
        Dim button As Button = CType(sender, Button)
        txtDisplay.Text &= button.Text
    End Sub

    Private Sub btnOperation_Click(sender As Object, e As EventArgs) Handles btnAdd.Click, btnSubtract.Click, btnMultiply.Click, btnDivide.Click
        Dim button As Button = CType(sender, Button)
        firstNumber = Decimal.Parse(txtDisplay.Text)
        txtDisplay.Clear()
        operation = button.Text
    End Sub

    Private Sub btnEquals_Click(sender As Object, e As EventArgs) Handles btnEquals.Click
        secondNumber = Decimal.Parse(txtDisplay.Text)
        Select Case operation
            Case "+"
                txtDisplay.Text = (firstNumber + secondNumber).ToString()
            Case "-"
                txtDisplay.Text = (firstNumber - secondNumber).ToString()
            Case "*"
                txtDisplay.Text = (firstNumber * secondNumber).ToString()
            Case "/"
                If secondNumber = 0 Then
                    MessageBox.Show("No se puede dividir por cero", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error)
                Else
                    txtDisplay.Text = (firstNumber / secondNumber).ToString()
                End If
        End Select
    End Sub

    Private Sub btnClear_Click(sender As Object, e As EventArgs) Handles btnClear.Click
        txtDisplay.Clear()
        firstNumber = 0
        secondNumber = 0
        operation = String.Empty
    End Sub
End Class
