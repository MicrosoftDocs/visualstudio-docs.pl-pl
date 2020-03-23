---
title: Interfejs API testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d949b8c73bb155b2e6fe4900c54c6d5314d26c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588814"
---
# <a name="how-to-use-the-load-test-api"></a>Jak: Korzystanie z interfejsu API testu obciążenia

Visual Studio obsługuje wtyczki testu obciążenia, które mogą kontrolować lub zwiększać test obciążenia. Wtyczki testu obciążenia są klasami zdefiniowanymi przez użytkownika, które implementują <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejs znajdujący się <xref:Microsoft.VisualStudio.TestTools.LoadTesting> w obszarze nazw. Wtyczki testu obciążenia umożliwiają niestandardową kontrolę testu obciążenia, na przykład przerywanie testu obciążenia po spełnieniu progu licznika lub progu błędu. Użyj właściwości w <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasie, aby uzyskać lub ustawić parametry testu obciążenia z kodu zdefiniowanego przez użytkownika. Użyj zdarzeń w <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasie, aby dołączyć delegatów do powiadomień, gdy test obciążenia jest uruchomiony.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Użyj przeglądarki obiektów, <xref:Microsoft.VisualStudio.TestTools.LoadTesting> aby sprawdzić obszar nazw. Edytory Visual C# i Visual Basic oferują obsługę intellisense do kodowania z klasami w obszarze nazw.

Można również utworzyć wtyczki do testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md) i [jak: Tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Aby użyć przestrzeni nazw LoadTesting

1. Otwórz projekt testu wydajności sieci web i obciążenia, który zawiera test obciążenia.

2. Dodaj visual C# lub visual basic projektu biblioteki klasy do rozwiązania testowego.

3. Dodaj odwołanie w projekcie testu wydajności sieci web i testu obciążenia do projektu biblioteki klas.

4. Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.LoadTestFramework w projekcie biblioteki klas.

5. W pliku klasy znajdującym się w `using` projekcie biblioteki klas dodaj instrukcję dla obszaru <xref:Microsoft.VisualStudio.TestTools.LoadTesting> nazw.

6. Utwórz klasę publiczną, <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> która implementuje interfejs.

7. Skompiluj projekt.

8. Dodaj nową wtyczkę testu obciążenia za pomocą Edytora testów obciążenia:

    1. Kliknij prawym przyciskiem myszy węzeł główny testu obciążenia, a następnie wybierz polecenie **Dodaj wtyczkę testu obciążenia**.

    2. Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki testu obciążenia.**

    3. W okienku **Właściwości dla wybranych wtyczek** ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Z wtyczek można udostępnić dowolną liczbę właściwości. Wystarczy, aby były one publiczne, settable i typu podstawowego, takich jak Liczba całkowita, Boolean lub String. Można również edytować właściwości wtyczki testu obciążenia później za pomocą okna **Właściwości.**

9. Uruchom test obciążenia.

     Aby uzyskać <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>implementację , zobacz [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Jak: Korzystanie z interfejsu API testu wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)
- [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
