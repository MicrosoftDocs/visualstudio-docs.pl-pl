---
title: 'CA2000: Likwiduj obiekty przed utratą zakresu'
ms.date: 05/14/2019
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
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804978"
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

### <a name="special-cases"></a>Specjalne przypadki

CA2000 reguły nie jest wyzwalana dla lokalnych obiektów następujących typów, nawet wtedy, gdy obiekt nie jest usuwane:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Przekazywanie obiektu z jednego z następujących typów do konstruktora, a następnie przypisując go do pola wskazuje *dispose przenoszenie własności* do nowo skonstruowanego typu. Oznacza to, że nowo skonstruowany typ odpowiada teraz do usuwania obiektu. Jeśli Twój kod przekazuje obiekt jednego z tych typów do konstruktora, nie naruszenia reguł CA2000 występuje nawet wtedy, gdy obiekt nie jest usuwane, zanim wszystkie odwołania do niego znajdą się poza zakresem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w obiekcie, zanim wszystkie odwołania do niego będą poza zakresem.

Możesz użyć [ `using` instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) w języku Visual Basic) do opakowania obiekty, które implementują <xref:System.IDisposable>. Obiekty, które są opakowane w ten sposób są automatycznie usuwane na końcu `using` bloku. Jednak nie powinien lub nie mogą być obsługiwane za pomocą w następujących sytuacjach `using` instrukcji:

- Aby zwrócić możliwy do likwidacji obiekt, obiekt musi być skonstruowany w `try/finally` block poza `using` bloku.

- Nie Inicjuj elementy członkowskie obiektu możliwe do rozporządzania w Konstruktorze typu `using` instrukcji.

- Kiedy konstruktory, które są chronione przez program obsługi wyjątków tylko jeden są zagnieżdżone w [nabycia część `using` instrukcji](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), błąd w Konstruktorze zewnętrzne może spowodować obiekt utworzony przez zagnieżdżone Konstruktor nigdy nie zamknięte. W poniższym przykładzie wystąpił błąd podczas <xref:System.IO.StreamReader> Konstruktor może spowodować <xref:System.IO.FileStream> obiektu nigdy nie jest zamknięty. CA2000 flagi naruszenie reguły, w tym przypadku.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Obiekty dynamiczne należy użyć obiektu w tle do implementowania wzorca usuwania dla <xref:System.IDisposable> obiektów.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, chyba że:

- Na obiekcie, który wywołuje wywołujesz metodę `Dispose`, takich jak <xref:System.IO.Stream.Close%2A>
- Metoda, która wywołała zwraca ostrzeżenie <xref:System.IDisposable> obiektu, który otacza obiekt
- Metody przydzielania nie mieć prawa własności do usuwania; oznacza to odpowiedzialność, można zlikwidować obiektu jest przenoszona do innego obiektu lub otok, który został utworzony w metodzie i zwracany do wywołującego

## <a name="related-rules"></a>Powiązane reguły

- [CA2213: Pola możliwe do rozporządzania należy rozporządzać](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202: Nie Likwiduj obiektów wiele razy](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Przykład

W przypadku wdrażania metodę, która zwraca obiekt rozporządzalny, użyj bloku try/finally bez blok catch, aby upewnić się, usunięciu obiektu. Za pomocą bloku try/finally, Zezwalaj na wyjątki, aby zostać wywołane w momencie błędu i upewnij się, że ten obiekt zostanie usunięty.

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

Domyślnie kompilator Visual Basic ma wszystkich operatorów arytmetycznych, sprawdzaj przepełnienie. W związku z tym, może zgłaszać żadnych operacji arytmetycznej języka Visual Basic <xref:System.OverflowException>. Może to prowadzić do nieoczekiwanych naruszeń w zasadach, takie jak CA2000. Na przykład następująca funkcja CreateReader1 dadzą naruszenie CA2000, ponieważ kompilator Visual Basic jest emitowania przepełnienie sprawdzanie instrukcji do dodania, który może zgłosić wyjątek, które spowodują TextWriter nie można usunąć.

Aby rozwiązać ten problem, można wyłączyć emitowania sprawdzania przepełnienia przez kompilator języka Visual Basic w projekcie lub zmodyfikować kod tak jak następującą funkcję CreateReader2.

Aby wyłączyć emitowania sprawdzania przepełnienia, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **skompilować**, kliknij przycisk **zaawansowane opcje kompilacji**, a następnie sprawdź, **Usuń nadmiaru**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)