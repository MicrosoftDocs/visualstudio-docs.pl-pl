---
title: Interfejs API testu wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d22c1962727d22af965c879de3ae5fea6d4e54af
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653296"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Instrukcje: korzystanie z interfejsu API testów wydajności sieci Web

Można napisać kod dla testów wydajności sieci Web. Interfejs API testu wydajności sieci Web służy do tworzenia kodowanych testów wydajności sieci Web, wtyczek testów wydajności sieci Web, wtyczek żądań, reguł wyodrębniania i reguł walidacji. Klasy tworzące te typy są klasami podstawowymi w tym interfejsie API. Inne typy w tym interfejsie API służą do obsługi tworzenia <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest>, <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> obiektów. Użyj przestrzeni nazw <xref:Microsoft.VisualStudio.TestTools.WebTesting>, aby utworzyć niestandardowe testy wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Możesz również użyć interfejsu API testu wydajności sieci Web do programistycznego tworzenia i zapisywania deklaratywnych testów wydajności sieci Web. Aby to zrobić, użyj klas <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> i <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer>.

> [!TIP]
> Użyj przeglądarki obiektów, aby przeanalizować <xref:Microsoft.VisualStudio.TestTools.WebTesting> przestrzeni nazw. Edytory wizualizacji C# i Visual Basic oferują obsługę funkcji IntelliSense do kodowania z klasami w przestrzeni nazw.

Możesz również utworzyć wtyczki dla testów obciążenia. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md) i [instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Aby użyć przestrzeni nazw WebTesting

1. Otwórz projekt testu wydajności i obciążenia sieci Web, który zawiera test wydajności sieci Web.

2. Dodaj projekt biblioteki C# klas wizualizacji lub Visual Basic do rozwiązania testowego.

3. Dodaj odwołanie w projekcie testu wydajności i obciążenia sieci Web do projektu biblioteki klas.

4. Dodaj odwołanie do biblioteki DLL Microsoft. VisualStudio. QualityTools. WebTestFramework w projekcie biblioteki klas.

5. W pliku klasy, który znajduje się w projekcie biblioteki klas, Dodaj instrukcję `using` dla przestrzeni nazw <xref:Microsoft.VisualStudio.TestTools.WebTesting>.

6. Utwórz klasę, która implementuje interfejs <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

7. Skompiluj projekt.

8. Dodaj nową wtyczkę testu wydajności sieci Web przy użyciu Edytor internetowego testu wydajnościowego:

    1. Wybierz pozycję **Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

         Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki testu sieci Web** .

    2. W obszarze **wybierz wtyczkę**wybierz klasę wtyczki testu wydajności sieci Web.

    3. We **właściwościach wybranego okienka wtyczek** Ustaw początkowe wartości dla wtyczki, które mają być używane w czasie wykonywania.

        > [!NOTE]
        > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Możesz również edytować właściwości wtyczki testu wydajności sieci Web później za pomocą okno Właściwości.

    4. Wybierz **przycisk OK**.

9. Uruchom test wydajności sieci Web.

     Aby zapoznać się z przykładową implementacją <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, zobacz [How to: Create a Web Performance test plug-in](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Instrukcje: korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md)
- [Instrukcje: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)