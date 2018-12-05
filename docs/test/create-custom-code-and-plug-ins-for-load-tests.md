---
title: Tworzenie niestandardowych kodów i wtyczek dla testów obciążenia w programie Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ed7b588d597626348b4c148c10dad165649b0468
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895759"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Tworzenie niestandardowych kodów i wtyczek dla testów obciążeniowych

Niestandardowa wtyczka używa kodu, który napiszesz i dołączysz to testu obciążeniowego lub testu wydajności sieci web. Można użyć interfejsu API testu obciążeniowego i interfejsu API testu wydajności sieci web do tworzenia niestandardowych wtyczek dla testów, aby rozszerzyć wbudowaną funkcjonalność. Możesz dodać wiele wtyczek do testu obciążeniowego.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Utwórz niestandardową wtyczkę dla testu obciążeniowego**: można użyć interfejsu API testu obciążeniowego, aby utworzyć niestandardową wtyczkę, która doda więcej funkcjonalności testowej do testu obciążeniowego.|-   [Porady: Korzystanie z API testu obciążenia](../test/how-to-use-the-load-test-api.md)<br />-   [Porady: tworzenie wtyczki testu obciążenia](../test/how-to-create-a-load-test-plug-in.md)|
|**Utwórz niestandardową wtyczkę dla testu wydajności sieci Web:** można użyć interfejsu API testu wydajności sieci web, aby utworzyć niestandardową wtyczkę, aby dodać więcej funkcjonalności testowej do testu wydajności sieci web, w tym na poziomie żądania. Można również utworzyć test usługi sieci web.<br /><br /> Ponadto można utworzyć sieci web dodatku plug-in rejestratora, można modyfikować test wydajności sieci web po zostało zapisane, ale przed pojawieniem się w sieci Web podglądzie wyników testu wydajności.|-   [Porady: Korzystanie z API testu wydajności sieci web](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Porady: tworzenie wtyczki testu wydajności sieci web](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Porady: tworzenie wtyczki na poziomie żądania](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Porady: Tworzenie nowego testu usługi internetowej](../test/how-to-create-a-web-service-test.md)<br />-   [Porady: tworzenie wtyczki rejestratora](../test/how-to-create-a-recorder-plug-in.md)|
|**Dodaj funkcje interfejsu użytkownika do podglądu wyników testu wydajności sieci Web:** możesz dodać więcej funkcji interfejsu użytkownika do podglądu wyników testu wydajności sieci Web za pomocą dodatku programu Visual Studio.|-   [Porady: Tworzenie dodatku programu Visual Studio dla sieci web wyników testu wydajności podglądu](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Tworzenie edytora niestandardowego ciała dokumentu HTTP:** można utworzyć niestandardowy edytor, aby edytować plik binarny lub ciąg znaków XML odpowiedzi http usługi sieci web.|-   [Porady: Tworzenie niestandardowego ciała dokumentu HTTP edytora dla edytora testów wydajności sieci web](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Tematy pomocy

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Zobacz także

- [Analizowanie wyników testów obciążenia](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generowanie i uruchom kodowany internetowy test wydajnościowy](../test/generate-and-run-a-coded-web-performance-test.md)