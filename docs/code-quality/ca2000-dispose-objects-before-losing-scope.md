---
title: 'CA2000: Likwiduj obiekty przed utratą zakresu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1d2e1e40945c3d3a60cdb633aac96c78dd92bc0e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936856"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Likwiduj obiekty przed utratą zakresu

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Obiekt lokalny <xref:System.IDisposable> typ jest tworzony, ale obiekt nie jest usuwane, zanim wszystkie odwołania do obiektu znajdą się poza zakresem.

## <a name="rule-description"></a>Opis reguły
 Jeśli możliwy do likwidacji obiekt nie zostanie jawnie zlikwidowany, zanim wszystkie odwołania do niego będą poza zakresem, obiekt zostanie zlikwidowany w nieokreślonym czasie gdy moduł odśmiecania pamięci uruchomi finalizatora obiektu. Ponieważ może wystąpić wyjątkowe zdarzenie, które uniemożliwi finalizatora obiektu, uruchamianie, obiekt powinien zostać jawnie zlikwidowany zamiast tego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w obiekcie, zanim wszystkie odwołania do niego będą poza zakresem.

 Należy zauważyć, że można użyć `using` — instrukcja (`Using` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) do opakowania obiekty, które implementują `IDisposable`. Obiekty, które są opakowane w ten sposób zostanie automatycznie usunięte z końcem `using` bloku.

 Poniżej przedstawiono kilka sytuacji, w którym za pomocą instrukcji nie jest wystarczająco, aby chronić interfejs IDisposable obiektów i może spowodować, że CA2000 występuje.

- Zwraca obiekt rozporządzalny wymaga, że obiekt jest konstruowany w bloku try/finally poza za pomocą bloku.

- Inicjowanie elementów członkowskich obiektu możliwe do rozporządzania, nie należy wykonywać w Konstruktorze przy użyciu instrukcji.

- Zagnieżdżanie konstruktorów, które są chronione tylko przez jeden wyjątek procedury obsługi. Na przykład

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     powoduje, że CA2000, ponieważ wystąpił błąd podczas tworzenia obiektu StreamReader może spowodować obiektu FileStream, nigdy nie jest zamknięty.

- Obiekty dynamiczne należy używać obiektu w tle do implementowania wzorca usuwania obiektów interfejsu IDisposable.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, jeśli wywołujesz metodę na obiekcie, który wywołuje `Dispose`, takich jak <xref:System.IO.Stream.Close%2A>, lub jeśli metoda, który spowodował ostrzeżenie zwraca obiekt interfejsu IDisposable otacza obiekt.

## <a name="related-rules"></a>Powiązane reguły
 [CA2213: Pola możliwe do rozporządzania należy rozporządzać](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Nie Likwiduj obiektów wiele razy](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Przykład

Przed zaimplementowaniem metodę, która zwraca obiekt rozporządzalny, użyj bloku try/finally bez blok catch, aby upewnić się, usunięciu obiektu. Za pomocą bloku try/finally, Zezwalaj na wyjątki, aby zostać wywołane w momencie błędu i upewnij się, że ten obiekt zostanie usunięty.

W metodzie OpenPort1 wywołania, które można otworzyć obiektu ISerializable portu SerialPort lub wywołanie SomeMethod może zakończyć się niepowodzeniem. CA2000 ostrzeżenie jest zgłaszane w tej implementacji.

W metodzie OpenPort2 dwa obiekty portu SerialPort są zadeklarowane i ustawienie wartości null:

- `tempPort`, która używany do sprawdzania, czy operacje metoda kończą się pomyślnie.

- `port`, która jest użyta wartość zwracaną metody.

`tempPort` Jest tworzony i otwierany `try` bloku i wszelkich innych wymaganych praca jest wykonywana w tym samym `try` bloku. Na koniec `try` blok, otwartego portu jest przypisany do `port` obiektu, który zostanie zwrócony i `tempPort` obiekt jest ustawiony na `null`.

`finally` Bloku sprawdza wartość `tempPort`. Jeśli nie ma wartość null, operacja w metodzie zakończyło się niepowodzeniem, a `tempPort` jest zamknięty, aby upewnić się, że wszystkie zasoby są zwalniane. Obiekt zwrócony portu będzie zawierać otwarty obiekt portu SerialPort operacje metody zakończyło się pomyślnie, czy będzie to być wartość null, jeśli operacja nie powiodła się.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Przykład
 Domyślnie [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora zawiera operatory arytmetyczne wszystkie sprawdzaj przepełnienie. W związku z tym, może zgłaszać żadnych operacji arytmetycznej języka Visual Basic <xref:System.OverflowException>. Może to prowadzić do nieoczekiwanych naruszeń w zasadach, takie jak CA2000. Na przykład następująca funkcja CreateReader1 dadzą naruszenie CA2000, ponieważ kompilator Visual Basic jest emitowania przepełnienie sprawdzanie instrukcji do dodania, który może zgłosić wyjątek, które spowodują TextWriter nie można usunąć.

 Aby rozwiązać ten problem, można wyłączyć emitowania sprawdzania przepełnienia przez kompilator języka Visual Basic w projekcie lub zmodyfikować kod tak jak następującą funkcję CreateReader2.

 Aby wyłączyć emitowania sprawdzania przepełnienia, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować**, kliknij przycisk **zaawansowane opcje kompilacji**, a następnie sprawdź, **Usuń nadmiaru**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)