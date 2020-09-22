---
title: Tworzenie wtyczki na poziomie żądania (testy wydajności sieci Web)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f136214b787820396fdbcff37f9f3b78574e9c8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810275"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Instrukcje: tworzenie wtyczki na poziomie żądania

*Żądania* to instrukcje deklaracyjne, które stanowią testy wydajności sieci Web. Wtyczki testów wydajności sieci Web umożliwiają izolowanie i ponowne użycie kodu poza głównymi instrukcjami deklaracyjne w teście wydajności sieci Web. Można utworzyć wtyczki i dodać je do indywidualnego żądania, a także do testu wydajności sieci Web, który go zawiera. Dostosowana  *wtyczka żądania* oferuje sposób wywoływania kodu, ponieważ określone żądanie jest uruchamiane w teście wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Każda wtyczka żądania testu wydajności sieci Web ma metodę preżądaną i metodę PostRequest. Po dołączeniu wtyczki żądania do określonego żądania HTTP przed odebraniem żądania zdarzenie wstępne zostanie wyzwolone i PostRequest zostanie wyzwolone po otrzymaniu odpowiedzi.

Możesz utworzyć dostosowaną wtyczkę żądania testu wydajności sieci Web, wprowadzając własną klasę z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> klasy bazowej.

Możesz użyć niestandardowych wtyczek do testowania wydajności sieci Web przy użyciu zarejestrowanych testów wydajności sieci Web. Niestandardowe wtyczki żądań testów wydajności sieci Web umożliwiają pisanie minimalnej ilości kodu w celu uzyskania wyższego poziomu kontroli nad testami wydajności sieci Web. Można ich również używać z kodowanymi testami wydajności sieci Web. Zobacz [generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Aby utworzyć wtyczkę na poziomie żądania

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie, wybierz polecenie **Dodaj** , a następnie wybierz pozycję **Nowy projekt**.

2. Utwórz nowy projekt **biblioteki klas** .

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder **odwołania** w nowej bibliotece klas i wybierz polecenie **Dodaj odwołanie**.

     Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

4. Wybierz kartę **.NET** , przewiń w dół, wybierz pozycję **Microsoft. VisualStudio. QualityTools. WebTestFramework** , a następnie wybierz przycisk **OK** .

     Odwołanie do **Microsoft. VisualStudio. QualityTools. WebTestFramework** jest dodawane do folderu **Reference** w **Eksplorator rozwiązań**.

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy górny węzeł projektu testu wydajności i obciążenia sieci Web, który zawiera test obciążenia, do którego chcesz dodać wtyczkę testową żądania testu wydajności sieci Web. Wybierz pozycję **Dodaj odwołanie**.

     **Zostanie wyświetlone okno dialogowe Dodawanie odwołania**.

6. Wybierz kartę **projekty** , wybierz **projekt Biblioteka klas** , a następnie wybierz przycisk **OK** .

7. W **edytorze kodu**Napisz kod wtyczki. Najpierw utwórz nową klasę publiczną, która pochodzi od <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> .

8. Zaimplementuj kod wewnątrz jednego lub obu <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> programów obsługi zdarzeń i. Przykładową implementację przedstawiono w następującej sekcji Przykład.

9. Po napisaniu kodu skompiluj nowy projekt.

10. Otwórz test wydajności sieci Web, do którego chcesz dodać wtyczkę żądania.

11. Kliknij prawym przyciskiem myszy żądanie, do którego chcesz dodać wtyczkę żądania, a następnie wybierz pozycję **Dodaj wtyczkę żądania**.

     Zostanie wyświetlone okno dialogowe **Dodaj wtyczkę żądania testu sieci Web** .

12. W obszarze **wybierz wtyczkę**wybierz nową wtyczkę.

13. We **właściwościach wybranego okienka wtyczek** Ustaw początkowe wartości dla wtyczki, które mają być używane w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również zmienić właściwości wtyczki testu wydajności sieci Web później za pomocą okno Właściwości.

14. Wybierz przycisk **OK**.

     Wtyczka jest dodawana do folderu **wtyczki żądania** , który jest folderem podrzędnym żądania HTTP.

    > [!WARNING]
    > Po uruchomieniu testu wydajności sieci Web lub testu obciążenia, który korzysta z wtyczki, może zostać wyświetlony błąd podobny do poniższego:
    >
    > **Żądanie nie powiodło się: wyjątek w \<plug-in> zdarzeniu: nie można załadować pliku lub zestawu " \<"Plug-in name".dll file> , Version = \<n.n.n.n> , Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może znaleźć określonego pliku.**
    >
    > Jest to spowodowane wprowadzeniem zmian w kodzie w dowolnych wtyczkach i utworzenie nowej wersji biblioteki DLL **(Version = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1. W projekcie testu wydajności i obciążenia sieci Web zobaczysz ostrzeżenie w odwołaniach. Usuń i Dodaj odwołanie do biblioteki DLL wtyczki.
    > 2. Usuń wtyczkę z testu lub odpowiedniej lokalizacji, a następnie dodaj ją ponownie.

## <a name="example"></a>Przykład

Można użyć poniższego kodu, aby utworzyć dostosowaną wtyczkę testu wydajności sieci Web, która wyświetla dwa okna dialogowe. Jedno okno dialogowe wyświetla adres URL, który jest skojarzony z żądaniem, do którego dołączono dodatek żądania. Drugie okno dialogowe wyświetla nazwę komputera agenta.

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
- [Kod reguły wyodrębniania niestandardowego dla testu wydajności sieci Web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod reguły niestandardowego sprawdzania poprawności dla testu wydajności sieci Web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
