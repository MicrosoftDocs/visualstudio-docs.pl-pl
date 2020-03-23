---
title: Interfejs API testu wydajności sieci Web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, using the API
- APIs, Web performance tests
ms.assetid: 93a6a1dd-663b-4ab5-8760-7d6b081561d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e869bc46997ffb6ebecae2aa3e49c3cb6b2582fa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594344"
---
# <a name="how-to-use-the-web-performance-test-api"></a>Jak: Korzystanie z interfejsu API testu wydajności sieci Web

Można napisać kod do testów wydajności sieci web. Interfejs API testu wydajności sieci Web służy do tworzenia kodowanych testów wydajności sieci Web, wtyczek testów wydajności sieci Web, wtyczek żądań, żądań, żądań, reguł wyodrębniania i reguł sprawdzania poprawności. Klasy, które tworzą te typy są podstawowe klasy w tym interfejsie API. Inne typy w tym interfejsie <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTest>API <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>są <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>używane <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule> do obsługi tworzenia , , , i obiektów. Obszar <xref:Microsoft.VisualStudio.TestTools.WebTesting> nazw służy do tworzenia niestandardowych testów wydajności sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Można również użyć interfejsu API testu wydajności sieci web do programowego tworzenia i zapisywania deklaratywnych testów wydajności sieci Web. Aby to zrobić, <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTest> <xref:Microsoft.VisualStudio.TestTools.WebTesting.DeclarativeWebTestSerializer> należy użyć i klas.

> [!TIP]
> Użyj przeglądarki obiektów, <xref:Microsoft.VisualStudio.TestTools.WebTesting> aby sprawdzić obszar nazw. Edytory Visual C# i Visual Basic oferują obsługę intellisense do kodowania z klasami w obszarze nazw.

Można również utworzyć wtyczki do testów obciążenia. Aby uzyskać więcej informacji, zobacz [Jak: Korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md) i [jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-use-the-webtesting-namespace"></a>Aby użyć obszaru nazw WebTesting

1. Otwórz projekt testu wydajności sieci web i obciążenia, który zawiera test wydajności sieci web.

2. Dodaj visual C# lub visual basic projektu biblioteki klasy do rozwiązania testowego.

3. Dodaj odwołanie w projekcie testu wydajności sieci web i testu obciążenia do projektu biblioteki klas.

4. Dodaj odwołanie do biblioteki DLL Microsoft.VisualStudio.QualityTools.WebTestFramework w projekcie biblioteki klas.

5. W pliku klasy, który znajduje się w `using` projekcie biblioteki klas, dodaj instrukcję dla obszaru <xref:Microsoft.VisualStudio.TestTools.WebTesting> nazw.

6. Utwórz klasę, która <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> implementuje interfejs.

7. Skompiluj projekt.

8. Dodaj nową wtyczkę testu wydajności sieci web przy użyciu Edytora testów wydajności sieci Web:

    1. Wybierz **pozycję Dodaj wtyczkę testu sieci Web** na pasku narzędzi.

         Zostanie wyświetlone okno dialogowe **Dodawanie wtyczki testu sieci Web.**

    2. W obszarze **Wybierz wtyczkę**wybierz klasę wtyczki testu wydajności sieci Web.

    3. W okienku **Właściwości dla wybranych wtyczek** ustaw wartości początkowe dla wtyczki do użycia w czasie wykonywania.

        > [!NOTE]
        > Można udostępnić dowolną liczbę właściwości każdej wtyczki. Wystarczy tylko ustawić je jako publiczne, możliwe do konfigurowania i mające typ podstawowy, np. Integer, Boolean lub String. Można również edytować właściwości wtyczki testu wydajności sieci web później za pomocą okna Właściwości.

    4. Wybierz pozycję **OK**.

9. Uruchom test wydajności sieci Web.

     Na przykład implementacja <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>, zobacz [Jak: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- [Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Jak: Korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md)
- [Jak: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)
