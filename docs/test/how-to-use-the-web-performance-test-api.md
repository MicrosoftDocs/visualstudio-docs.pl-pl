---
title: Test wydajności sieci Web interfejsu API
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ab103b11659ee1e73537f6f41ff1fe0e6ed32076
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978565"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Instrukcje: Użyj interfejsu API testu wydajności sieci web

Można napisać kod dla testów wydajności sieci web. Test wydajności sieci web interfejsu API jest używany do utworzenia kodowanego testu wydajności WWW, sieci web wydajności wtyczki testu, wtyczki żądania, żądania, reguły wyodrębniania, reguł sprawdzania poprawności. Klasy, które tworzą te typy są klasy podstawowe, w tym interfejsie API. Inne typy w tym interfejsie API są używane do obsługi tworzenia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>, i <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> obiektów. Możesz użyć <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw, aby tworzyć niestandardowe internetowe testy wydajnościowe.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Aby programowo utworzyć i zapisać testów wydajności sieci web deklaratywne umożliwia także interfejsu API testu wydajności sieci web. Aby to zrobić, należy użyć <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> klasy.

> [!TIP]
> Używanie przeglądarki obiektów do zbadania <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw. Edytory zarówno Visual C# i Visual Basic oferuje obsługę funkcji IntelliSense na kodowanie przy użyciu klas w przestrzeni nazw.

Można również utworzyć wtyczek dla testów obciążenia. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z API testu obciążeniowego](../test/how-to-use-the-load-test-api.md) i [jak: Tworzenie wtyczki testu obciążeniowego](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Użycie tej przestrzeni nazw WebTesting

1. Otwórz wydajności sieci web i obciążenia projektu testowego, który zawiera test wydajności sieci web.

2. Dodaj Visual C# lub projekt biblioteki klas języka Visual Basic do rozwiązania testu.

3. Dodaj odwołanie w projekcie testu wydajności i obciążenia sieci web do projektu biblioteki klas.

4. Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.WebTestFramework w projekcie biblioteki klas.

5. W pliku klasy, który znajduje się w projekcie biblioteki klas, Dodaj `using` poufności informacji dotyczące <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw.

6. Utwórz klasę, która implementuje <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> interfejsu.

7. Skompiluj projekt.

8. Dodaj nowy test wydajności sieci web wtyczki za pomocą edytora testu wydajności sieci Web:

    1. Wybierz **Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

         **Dodaj wtyczkę testu sieci Web** zostanie wyświetlone okno dialogowe.

    2. W obszarze **Wybierz wtyczkę**, zaznacz klasę wtyczki testu wydajności sieci web.

    3. W **właściwości wybranych wtyczek** okienko, ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Właściwości wtyczki testu wydajności sieci web można również edytować później za pomocą okna właściwości.

    4. Wybierz **OK**.

9. Uruchom test wydajności sieci web.

     Przykład wykonania <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, zobacz [jak: Tworzenie wtyczki testu wydajności sieci web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: Użyj interfejsu API testu obciążeniowego](../test/how-to-use-the-load-test-api.md)
- [Instrukcje: Tworzenie wtyczki testu wydajności sieci web](../test/how-to-create-a-web-performance-test-plug-in.md)