---
title: Tworzenie wtyczki dla testów wydajności sieci web na poziomie żądania
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: aece31feb6e9b84fd2a23900f1a5da4d1194b05a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917873"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Instrukcje: Tworzenie wtyczki na poziomie żądania

*Żądania* są deklaratywne instrukcje, które stanowią testów wydajności sieci web. Wtyczki sieci Web wydajności testów umożliwiają izolowanie i ponowne użycie kodu poza głównym deklaracyjne oświadczeń do testu wydajności sieci web. Można tworzyć dodatki plug-in i dodać je do pojedynczego żądania także do testu wydajności sieci web, która go zawiera. Dostosowany *wtyczkę żądania* umożliwia wywoływanie kodu podczas uruchamiania poszczególnych żądań w teście wydajności sieci web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Wtyczka każde żądanie testu wydajności sieci web ma PreRequest metody i PostRequest metody. Po dołączeniu wtyczki obsługi żądań do żądania http określonej PreRequest zdarzenie zostanie wyzwolone przed wystawić żądania i PostRequest uruchamiane po otrzymaniu odpowiedzi.

Można utworzyć żądanie testu wydajności sieci web dostosowane wtyczki wyprowadzanie klasy z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> klasy bazowej.

Za pomocą dostosowanych web wydajności żądania wtyczki testu za pomocą testów wydajności sieci web, które zostały zarejestrowane. Niestandardowe sieci web wydajności żądania wtyczki testu umożliwiają minimalnej ilości kodu, aby osiągnąć większy poziom kontroli nad testy wydajności sieci web. Jednak umożliwia także je z kodowanego testu wydajności www. Zobacz [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>Do tworzenie wtyczki na poziomie żądania

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie, wybierz **Dodaj** , a następnie wybierz **nowy projekt**.

     **Dodaj nowy projekt** zostanie wyświetlone okno dialogowe.

2.  W obszarze **zainstalowane szablony**, wybierz opcję **Visual C#**.

3.  Na liście szablonów wybierz **biblioteki klas**.

4.  W **nazwa** polu tekstowym wpisz nazwę dla klasy i wybierz **OK**.

     Nowy projekt biblioteki klas zostanie dodany do **Eksploratora rozwiązań** i Nowa klasa pojawi się w **Edytor kodu**.

5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** folderu w nową bibliotekę klas i wybierz pozycję **Dodaj odwołanie**.

     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

6.  Wybierz **.NET** , przewiń w dół, a następnie wybierz **Microsoft.VisualStudio.QualityTools.WebTestFramework** , a następnie wybierz **OK**

     Odwołanie do **Microsoft.VisualStudio.QualityTools.WebTestFramework** jest dodawany do **odwołania** folderu w **Eksploratora rozwiązań**.

7.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy górny węzeł wydajności sieci web i załadować projekt testowy, który zawiera test obciążeniowy, do którego chcesz dodać wydajności testu żądania wtyczkę testu sieci web. Wybierz **Dodaj odwołanie**.

     **Zostanie wyświetlone okno dialogowe Dodaj odwołanie**.

8.  Wybierz **projektów** zaznacz **projekt biblioteki klas** , a następnie wybierz **OK** .

9. W **Edytor kodu**, wpisać kod wtyczkę. Najpierw utwórz nową klasę publiczną, która pochodzi od klasy <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>.

10. Implementowanie kod wewnątrz co najmniej jeden z <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> procedury obsługi zdarzeń. Przykładową implementację przedstawiono w następującej sekcji Przykład.

11. Po napisaniu kodu skompiluj nowy projekt.

12. Otwórz test wydajności sieci web, do której chcesz dodać wtyczkę żądania.

13. Kliknij prawym przyciskiem myszy żądanie, do którego chcesz dodać żądania wtyczki i wybierz pozycję **Dodaj wtyczkę żądania**.

     **Dodaj wtyczkę żądania testu sieci Web** zostanie wyświetlone okno dialogowe.

14. W obszarze **Wybierz wtyczkę**, wybierz nową wtyczkę.

15. W **właściwości wybranych wtyczek** okienko, ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

    > [!NOTE]
    > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci web można również zmienić później, przy użyciu okna właściwości.

16. Wybierz **OK**.

     Wtyczka zostanie dodana do **wtyczki żądania** folder, który jest folder podrzędny żądania HTTP.

    > [!WARNING]
    > Możesz otrzymać błąd podobny do następującego po uruchomieniu testu wydajności sieci web lub testu obciążenia, który korzysta z Twojej wtyczki:
    >
    > **Żądanie nie powiodło się: Wyjątek w \<wtyczki > zdarzenia: Nie można załadować pliku lub zestawu "\<pliku dll"Nazwa wtyczki">, wersja =\<n.n.n.n >, Culture = neutral, PublicKeyToken = null" lub jednej z jego zależności. System nie może odnaleźć określonego pliku.**
    >
    > Dzieje się tak Jeśli wprowadzasz zmiany kodu do dowolnego typu plug-ins i utworzyć nową wersję biblioteki DLL **(wersja = 0.0.0.0)**, ale wtyczka nadal odwołuje się do oryginalnej wersji wtyczki. Aby rozwiązać ten problem, wykonaj następujące kroki:
    >
    > 1.  W wydajności sieci web i obciążenia projektu testowego zostanie wyświetlone ostrzeżenie w odwołaniach. Usuń i ponownie Dodaj odwołanie do biblioteki DLL dodatku plug-in.
    > 2.  Usuń dodatek plug-in z testu lub odpowiedniej lokalizacji, a następnie dodaj go ponownie.

## <a name="example"></a>Przykład

Poniższy kod służy do tworzenia dostosowanych wydajności wtyczkę testu sieci web wyświetlający dwóch okien dialogowych. Jeden okno dialogowe wyświetla adres URL, który jest skojarzony z tym żądaniem, do którego dołączyć dodatku żądania. Drugie okno dialogowe wyświetla nazwę komputera agenta.

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

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kod niestandardowej reguły wyodrębniania dla testów wydajności sieci web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kod niestandardowej reguły walidacji dla testów wydajności sieci web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Instrukcje: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
- [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md)