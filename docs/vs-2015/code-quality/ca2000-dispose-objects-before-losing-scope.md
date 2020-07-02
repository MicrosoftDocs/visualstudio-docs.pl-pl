---
title: 'CA2000: Usuń obiekty przed utratą zakresu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534774"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Likwiduj obiekty przed utratą zakresu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Obiekt lokalny <xref:System.IDisposable> typu jest tworzony, ale obiekt nie jest usuwany, zanim wszystkie odwołania do obiektu znajdują się poza zakresem.

## <a name="rule-description"></a>Opis reguły
 Jeśli obiekt do udostępnienia nie zostanie jawnie usunięty, zanim wszystkie odwołania do niego będą poza zakresem, obiekt zostanie usunięty w pewnym nieokreślonym czasie, gdy moduł zbierający elementy bezużyteczne uruchomi finalizator obiektu. Ze względu na to, że może wystąpić wyjątkowe zdarzenie uniemożliwiające uruchomienie finalizatora obiektu, obiekt powinien zostać jawnie usunięty.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj <xref:System.IDisposable.Dispose%2A> dla obiektu, zanim wszystkie odwołania do niego znajdują się poza zakresem.

 Należy zauważyć, że można użyć `using` instrukcji ( `Using` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) do zawijania obiektów, które implementują `IDisposable` . Obiekty, które są opakowane w ten sposób, zostaną automatycznie usunięte po zamknięciu `using` bloku.

 Poniżej wymieniono sytuacje, w których instrukcja using nie wystarcza do ochrony obiektów IDisposable i może spowodować wystąpienie CA2000.

- Zwrócenie obiektu jednorazowego wymaga, aby obiekt został skonstruowany w bloku try/finally poza blokiem using.

- Nie należy wykonywać inicjowania składowych jednodostępnego obiektu w konstruktorze instrukcji using.

- Zagnieżdżanie konstruktorów, które są chronione tylko przez jeden program obsługi wyjątków. Na przykład

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     powoduje wystąpienie CA2000, ponieważ błąd w konstrukcji obiektu StreamReader może spowodować, że obiekt FileStream nie zostanie zamknięty.

- Obiekty dynamiczne powinny używać obiektu Shadow do implementowania wzorca Dispose obiektów IDisposable.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, chyba że metoda wywoływana w obiekcie nie ma metody wywołującej `Dispose` , takiej jak <xref:System.IO.Stream.Close%2A> , lub jeśli metoda, która spowodowała ostrzeżenie, zwraca obiekt IDisposable, zawija obiekt.

## <a name="related-rules"></a>Powiązane reguły
 [CA2213: Pola możliwe do likwidacji należy likwidować](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: Nie likwiduj obiektów wielokrotnie](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Przykład
 W przypadku implementowania metody, która zwraca obiekt jednorazowy, należy użyć bloku try/finally bez bloku catch, aby upewnić się, że obiekt został usunięty. Za pomocą bloku try/finally można wypróbować wyjątki w punkcie błędu i upewnić się, że obiekt został usunięty.

 W metodzie OpenPort1 wywołanie otwierania obiektu ISerializable klasy SerialPort lub wywołanie SomeMethod może zakończyć się niepowodzeniem. W tej implementacji zgłoszono ostrzeżenie CA2000.

 W metodzie OpenPort2 są zadeklarowane dwa obiekty klasy SerialPort i mają ustawioną wartość null:

- `tempPort`, który jest używany do testowania, że operacje metody powiodły się.

- `port`, która jest używana dla wartości zwracanej przez metodę.

  `tempPort`Jest konstruowany i otwarty w `try` bloku, a wszystkie inne wymagane zadania są wykonywane w tym samym `try` bloku. Na końcu `try` bloku otwarty port zostanie przypisany do `port` obiektu, który będzie zwracany, a `tempPort` obiekt jest ustawiony na `null` .

  `finally`Blok sprawdza wartość `tempPort` . Jeśli wartość nie jest równa null, operacja w metodzie zakończyła się niepowodzeniem i `tempPort` jest ZAMKNIĘTA, aby upewnić się, że wszystkie zasoby zostały wydane. Zwrócony obiekt portu będzie zawierał otwarty obiekt klasy SerialPort, jeśli operacje metody zakończyły się powodzeniem lub jeśli operacja nie powiedzie się, będzie mieć wartość null.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Przykład
 Domyślnie [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilator ma wszystkie operatory arytmetyczne w przypadku przepełnienia. W związku z tym każda operacja arytmetyczna Visual Basic może zgłosić <xref:System.OverflowException> . Może to prowadzić do nieoczekiwanych naruszeń reguł, takich jak CA2000. Na przykład następująca funkcja CreateReader1 wygeneruje naruszenie zasad CA2000, ponieważ kompilator Visual Basic emituje instrukcję sprawdzającą przepełnienie dla dodatku, który mógłby zgłosić wyjątek, który mógłby spowodować, że StreamReader nie zostanie usunięte.

 Aby rozwiązać ten problem, można wyłączyć emitowanie sprawdzania przepełnienia przez kompilator Visual Basic w projekcie lub zmodyfikować kod jak w następującej funkcji CreateReader2.

 Aby wyłączyć emitowanie sprawdzania przepełnienia, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań a następnie kliknij pozycję **Właściwości**. Kliknij przycisk **Kompiluj**, kliknij pozycję **Zaawansowane opcje kompilacji**, a następnie zaznacz pole wyboru **Usuń operacje przepełnienia liczby całkowitej**.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable>Usuń [wzorzec](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)