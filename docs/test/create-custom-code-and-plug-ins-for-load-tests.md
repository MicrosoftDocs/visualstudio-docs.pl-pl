---
title: Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3519a593182c199cc9f7a92cfb77e9c79bd1a9ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590101"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych

Niestandardowa wtyczka używa kodu, który piszesz i dołączasz do testu obciążenia lub testu wydajności sieci Web. Za pomocą interfejsu API testu obciążenia i interfejsu API testu wydajności sieci web można utworzyć niestandardowe wtyczki do testów w celu rozszerzenia do wbudowanej funkcji. Do testu obciążenia można dodać wiele wtyczek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Utwórz niestandardową wtyczkę dla testu obciążenia:** Możesz użyć interfejsu API testu obciążenia, aby utworzyć niestandardową wtyczkę, aby dodać więcej funkcji testowania do testu obciążenia.|-   [Jak: Korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md)<br />-   [Jak: Tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)|
|**Utwórz niestandardową wtyczkę dla testu wydajności sieci Web:** Za pomocą interfejsu API testu wydajności sieci web można utworzyć niestandardową wtyczkę, aby dodać więcej funkcji testowania do testu wydajności sieci Web, w tym na poziomie żądania. Można również utworzyć test usługi sieci web.<br /><br /> Ponadto można utworzyć wtyczkę rejestratora sieci web, która może modyfikować test wydajności sieci Web po jego zarejestrowaniu, ale zanim pojawi się w przeglądarce wyników testu wydajności sieci Web.|-   [Jak: Korzystanie z interfejsu API testu wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Jak: Tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Jak: Tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Jak: Tworzenie testu usługi sieci web](../test/how-to-create-a-web-service-test.md)<br />-   [Jak: Tworzenie wtyczki rejestratora](../test/how-to-create-a-recorder-plug-in.md)|
|**Dodaj funkcje interfejsu użytkownika do podglądu wyników testów wydajności sieci Web:** Można dodać więcej funkcji interfejsu użytkownika do Przeglądarki wyników testów wydajności sieci Web przy użyciu dodatku visual studio.|-   [Jak: Tworzenie dodatku programu Visual Studio dla przeglądarki wyników testów wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Tworzenie niestandardowego edytora treści HTTP:** Można utworzyć edytor niestandardowy do edycji odpowiedzi binarnych lub ciągów http XML z usługi sieci web.|-   [Jak: Tworzenie niestandardowego edytora treści HTTP dla edytora testów wydajności sieci Web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Dokumentacja

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testu obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
