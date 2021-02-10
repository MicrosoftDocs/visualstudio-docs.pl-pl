---
title: Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych
description: Dowiedz się, jak za pomocą interfejsu API testu obciążenia i interfejsu API testów wydajności sieci Web utworzyć niestandardowe wtyczki dla testów, które mają zostać rozszerzone do wbudowanej funkcji.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 040ca84d5da9019da87f0dfddc89cfc6b1aa043e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964449"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych

Niestandardowa Wtyczka używa kodu, który można napisać i dołączyć do testu obciążenia lub testu wydajności sieci Web. Możesz użyć interfejsu API testu obciążenia i interfejsu API testu wydajności sieci Web, aby utworzyć niestandardowe wtyczki dla testów, aby rozszerzyć je do wbudowanej funkcji. Do testu obciążenia można dodać wiele wtyczek.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Utwórz niestandardową wtyczkę dla testu obciążenia**: możesz użyć interfejsu API testu obciążenia, aby utworzyć niestandardową wtyczkę, aby dodać więcej funkcji testowania do testu obciążenia.|-   [Instrukcje: korzystanie z interfejsu API testu obciążenia](../test/how-to-use-the-load-test-api.md)<br />-   [Instrukcje: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)|
|**Utwórz niestandardową wtyczkę dla testu wydajności sieci Web:** Korzystając z interfejsu API testów wydajności sieci Web, można utworzyć niestandardową wtyczkę, aby dodać więcej funkcji testowania do testu wydajności sieci Web, w tym na poziomie żądania. Możesz również utworzyć test usługi sieci Web.<br /><br /> Ponadto można utworzyć wtyczkę rejestratora sieci Web, która może zmodyfikować test wydajności sieci Web po jego zarejestrowaniu, ale przed pojawieniem się w Podgląd wyników internetowego testu wydajnościowego.|-   [Instrukcje: korzystanie z interfejsu API testów wydajności sieci Web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Instrukcje: tworzenie wtyczki testu wydajności sieci Web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Instrukcje: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Instrukcje: Tworzenie testu usługi sieci Web](../test/how-to-create-a-web-service-test.md)<br />-   [Instrukcje: tworzenie wtyczki rejestratora](../test/how-to-create-a-recorder-plug-in.md)|
|**Dodaj funkcje interfejsu użytkownika do przeglądarki wyniki testów wydajności sieci Web:** Możesz dodać więcej funkcji interfejsu użytkownika do przeglądarki Wyniki testów wydajności sieci Web przy użyciu dodatku programu Visual Studio.|-   [Instrukcje: Tworzenie dodatku programu Visual Studio dla przeglądarki wyników testów wydajności sieci Web](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Utwórz niestandardowy Edytor treści http:** Można utworzyć niestandardowy Edytor, aby edytować dane binarne lub ciągi XML http z usługi sieci Web.|-   [Instrukcje: Tworzenie niestandardowego edytora treści HTTP dla edytora testów wydajności sieci Web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Dokumentacja

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Zobacz też

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generowanie i uruchamianie kodowanego testu wydajności sieci Web](../test/generate-and-run-a-coded-web-performance-test.md)
