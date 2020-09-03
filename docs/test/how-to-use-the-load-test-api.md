---
title: Interfejs API testu obciążenia
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- code, load tests
- plug-ins, load test
- APIs, load tests
ms.assetid: e15567bc-1f21-4feb-b81d-f17ba35cfde5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1fc3ff1aa238249f7425c61b5b28d2a96e299fec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287106"
---
# <a name="how-to-use-the-load-test-api"></a>Instrukcje: korzystanie z interfejsu API testu obciążenia

Program Visual Studio obsługuje wtyczki testów obciążenia, które mogą kontrolować lub ulepszać test obciążenia. Wtyczki testów obciążenia są klasami zdefiniowanymi przez użytkownika, które implementują <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejs znaleziony w <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw. Wtyczki testów obciążenia zezwalają na niestandardową kontrolkę testu obciążenia, na przykład przerywanie testu obciążenia, gdy zostanie spełniony licznik lub próg błędu. Użyj właściwości <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> klasy w celu pobrania lub ustawienia parametrów testu obciążenia z kodu zdefiniowanego przez użytkownika. Użyj zdarzeń z klasy, <xref:Microsoft.VisualStudio.TestTools.LoadTesting.LoadTest> Aby dołączyć delegatów do powiadomień, gdy test obciążenia jest uruchomiony.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!TIP]
> Użyj przeglądarki obiektów, aby przeanalizować <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeń nazw. Edytory Visual C# i Visual Basic oferują obsługę funkcji IntelliSense do kodowania z klasami w przestrzeni nazw.

Możesz również utworzyć wtyczki dla testów wydajności sieci Web. Aby uzyskać więcej informacji, zobacz [jak: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md) i [instrukcje: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md).

## <a name="to-use-the-loadtesting-namespace"></a>Aby użyć przestrzeni nazw LoadTesting

1. Otwórz projekt testu wydajności i obciążenia sieci Web, który zawiera test obciążenia.

2. Dodaj projekt biblioteki klas Visual C# lub Visual Basic do rozwiązania testowego.

3. Dodaj odwołanie w projekcie testu wydajności i obciążenia sieci Web do projektu biblioteki klas.

4. Dodaj odwołanie do biblioteki DLL Microsoft. VisualStudio. QualityTools. LoadTestFramework w projekcie biblioteki klas.

5. W pliku klasy znajdującym się w projekcie biblioteki klas Dodaj `using` instrukcję dla <xref:Microsoft.VisualStudio.TestTools.LoadTesting> przestrzeni nazw.

6. Utwórz klasę publiczną, która implementuje <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> interfejs.

7. Skompiluj projekt.

8. Dodaj nową wtyczkę testu obciążenia przy użyciu Edytor testu obciążeniowego:

    1. Kliknij prawym przyciskiem myszy węzeł główny testu obciążenia, a następnie wybierz polecenie **Dodaj wtyczkę testu obciążenia**.

    2. Zostanie wyświetlone okno dialogowe **Dodaj wtyczkę testu obciążenia** .

    3. We **właściwościach wybranego okienka wtyczek** Ustaw początkowe wartości dla wtyczki, które mają być używane w czasie wykonywania.

        > [!NOTE]
        > Można uwidocznić dowolną liczbę właściwości z wtyczek. Po prostu ustaw je jako publiczne, settable i typu podstawowego, takie jak Integer, Boolean lub String. Właściwości wtyczki testu obciążenia można również edytować później przy użyciu okna **Właściwości** .

9. Uruchom test obciążenia.

     Aby uzyskać implementację programu <xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin> , zobacz [How to: Create a test Load plug-in](../test/how-to-create-a-load-test-plug-in.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: korzystanie z interfejsu API testów wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)
- [Instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)
