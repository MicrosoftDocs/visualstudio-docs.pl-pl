---
title: Tworzenie wtyczki na poziomie żądania do testów wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e57f92a3f45983321a866f3524974ea99dba82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589160"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Jak: Tworzenie wtyczki na poziomie żądania

*Żądania* są deklaratywnymi instrukcjami, które stanowią testy wydajności sieci Web. Wtyczki testów wydajności sieci Web umożliwiają izolowanie i ponowne użycie kodu poza głównymi instrukcjami deklaratywnymi w teście wydajności sieci Web. Można utworzyć wtyczki i dodać je do pojedynczego żądania, a także do testu wydajności sieci Web, który go zawiera. Dostosowana *wtyczka żądania* oferuje sposób wywołania kodu, ponieważ określone żądanie jest uruchamiane w teście wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Każda wtyczka żądania testu wydajności sieci web ma metodę PreRequest i metodę PostRequest. Po dołączeniu wtyczki żądania do określonego żądania http, Zdarzenie PreRequest zostanie zwolniony przed wystawieniem żądania i PostRequest zwolniony po odebraniu odpowiedzi.

Można utworzyć wtyczkę żądania testu wydajności sieci web, wyprowadzając <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> własną klasę z klasy podstawowej.

Można użyć dostosowanych wtyczek żądań testów wydajności sieci web z zarejestrowanymi testami wydajności sieci Web. Dostosowane wtyczki żądania testu wydajności sieci Web umożliwiają zapisanie minimalnej ilości kodu w celu uzyskania większego poziomu kontroli nad testami wydajności sieci Web. Można ich jednak również używać z kodowanych testów wydajności sieci Web. Zobacz [Generowanie i uruchamianie kodowanych testów wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Aby utworzyć wtyczkę na poziomie żądania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz pozycję **Dodaj,** a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **biblioteki klas.**

3. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy folder **Odwołania** w nowej bibliotece klas i wybierz polecenie **Dodaj odwołanie**.

     Zostanie wyświetlone okno dialogowe **Dodawanie odwołania.**

4. Wybierz kartę **.NET,** przewiń w dół, wybierz pozycję **Microsoft.VisualStudio.QualityTools.WebTestFramework,** a następnie wybierz przycisk **OK**

     Odwołanie do **pliku Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawane do folderu **Odwołania** w **Eksploratorze rozwiązań**.

5. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy górny węzeł projektu testu wydajności sieci web i obciążenia zawierający test obciążenia, do którego chcesz dodać wtyczkę testową żądania testu wydajności sieci Web. Wybierz **pozycję Dodaj odniesienie**.

     Zostanie **wyświetlone okno dialogowe Dodawanie odwołania**.

6. Wybierz kartę **Projekty,** wybierz **projekt biblioteki klas,** a następnie wybierz przycisk **OK** .

7. W **Edytorze kodów**napisz kod wtyczki. Najpierw utwórz nową klasę publiczną, która wywodzi się z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

8. Zaimplementuj kod <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> wewnątrz jednego lub obu programów obsługi zdarzeń i. Przykładową implementację przedstawiono w następującej sekcji Przykład.

9. Po napisaniu kodu skompiluj nowy projekt.

10. Otwórz test wydajności sieci Web, do którego chcesz dodać wtyczkę żądania.

11. Kliknij prawym przyciskiem myszy żądanie, do którego chcesz dodać wtyczkę żądania, a następnie wybierz pozycję **Dodaj wtyczkę żądania**.

     Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki Żądania testu sieci Web.**

12. W obszarze **Wybierz wtyczkę**wybierz nową wtyczkę.

13. W okienku **Właściwości dla wybranych wtyczek** ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Można również zmienić właściwości wtyczki testu wydajności sieci web później za pomocą okna Właściwości.

14. Wybierz pozycję **OK**.

     Wtyczka jest dodawana do folderu **Wtyczki żądań,** który jest folderem podrzędnym żądania HTTP.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który używa wtyczki, może pojawić się błąd podobny do następującego:
    >
    > **Żądanie nie powiodło \<się: Wyjątek w> zdarzenia dodatku\<plug-in: nie można załadować pliku lub zestawu\<' "Nazwa wtyczki".dll plik>, Version= n.n.n.n>, Culture=neutral, PublicKeyToken=null' lub jedną z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie do któregokolwiek z wtyczek i utworzeniem nowej wersji biblioteki DLL **(Version=0.0.0.0),** ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności sieci web i obciążenia zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie dodaj odwołanie do biblioteki DLL wtyczek.
    > 2. Wyjmij wtyczkę z testu lub w odpowiedniej lokalizacji, a następnie dodaj ją z powrotem.

## <a name="example"></a>Przykład

Za pomocą następującego kodu można utworzyć dostosowaną wtyczkę testu wydajności sieci Web, która wyświetla dwa okna dialogowe. W jednym oknie dialogowym jest wyświetlany adres URL skojarzony z żądaniem, do którego dołącza się dodatek żądania. W drugim oknie dialogowym wyświetlana jest nazwa komputera agenta.

> [!NOTE]
> Poniższy kod wymaga, aby dodać odwołanie do przestrzeni nazw System.Windows.Forms.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kodowania niestandardowej reguły wyodrębniania dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodowania niestandardowej reguły sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
