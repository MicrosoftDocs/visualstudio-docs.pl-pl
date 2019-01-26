---
title: Rozszerzanie kodowanych testów interfejsu użytkownika i nagrywania akcji
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a2c3ddb18e2414080b7d6354d1e04fc97275b12e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019414"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Rozszerzanie kodowanych testów interfejsu użytkownika i nagrywania akcji

Struktura testowania kodowane testy interfejsu użytkownika i nagrywania akcji nie obsługuje Każdy przykładowy interfejs użytkownika. Nie obsługuje określonego interfejsu użytkownika, który ma zostać przetestowana. Na przykład bezpośrednio nie można utworzyć kodowany test interfejsu użytkownika lub nagranie akcji dla arkusza kalkulacyjnego programu Microsoft Excel. Można jednak utworzyć własne rozszerzenie struktury kodowanego testu interfejsu użytkownika, obsługującego określonych interfejs użytkownika dzięki wykorzystaniu możliwości rozszerzania Framework kodowanego testu interfejsu użytkownika.

![Architektura testu interfejsu użytkownika](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Przykładowe rozszerzenie do testowania programu Microsoft Excel

To [wpis w blogu](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) zawiera link do [Przykładowe rozszerzenie](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) Framework kodowanego testu interfejsu użytkownika. Można również przeglądać całą [serię wpis w blogu coded UI test rozszerzalności](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> Przykład jest przeznaczony do użytku z programem Microsoft Excel 2010. Może, może nie działać z innymi wersjami programu Excel.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)