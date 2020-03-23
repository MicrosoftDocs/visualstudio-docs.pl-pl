---
title: Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 05ccb885c799bf2bfd2e3868b80226eca726cc31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589555"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji

Struktura testowania kodowanych testów interfejsu użytkownika i nagrań akcji nie obsługuje każdego możliwego interfejsu użytkownika. Może nie obsługiwać określonego interfejsu użytkownika, który chcesz przetestować. Na przykład nie można natychmiast utworzyć zakodowany test interfejsu użytkownika lub nagrywania akcji dla arkusza kalkulacyjnego programu Microsoft Excel. Można jednak utworzyć własne rozszerzenie do struktury testów kodowanych interfejsu użytkownika, która obsługuje określony interfejs użytkownika, korzystając z rozszerzalności kodowanych struktury testów interfejsu użytkownika.

![Architektura testu interfejsu użytkownika](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Przykładowe rozszerzenie do testowania programu Microsoft Excel

Ten [wpis w blogu](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/3-introducing-sample-excel-extension/) zawiera łącze do [przykładowego rozszerzenia](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) dla zakodowanych struktury testu interfejsu użytkownika. Można również wyświetlić całą [serię wpisów w blogu dla rozszerzalności testu kodowanych interfejsu użytkownika](https://blogs.msdn.microsoft.com/gautamg/2010/01/05/series-on-coded-ui-test-extensibility/).

> [!NOTE]
> Próbka jest przeznaczona do użytku z programem Microsoft Excel 2010. Może lub nie może działać z innymi wersjami programu Excel.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestactionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
- [Najważniejsze wskazówki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
