---
title: Poszerzenie kodowanych testów interfejsu użytkownika i nagrań akcji
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c8efead1712ace2f533cb9075ea7a4c5305289a4
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036083"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Poszerzenie kodowanych testów interfejsu użytkownika i nagrań akcji

Struktura testowania dla kodowanych testów interfejsu użytkownika i nagrań akcji nie obsługuje każdego możliwego interfejsu użytkownika. Może nie obsługiwać określonego interfejsu użytkownika, który ma zostać przetestowany. Na przykład nie można natychmiast utworzyć kodowanego testu interfejsu użytkownika lub rejestrowania akcji dla arkusza kalkulacyjnego programu Microsoft Excel. Można jednak utworzyć własne rozszerzenie dla struktury kodowanego testu interfejsu użytkownika, która obsługuje określony interfejs użytkownika, wykorzystując rozszerzalność kodowanego środowiska testowania interfejsu użytkownika.

![Architektura testu interfejsu użytkownika](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Przykładowe rozszerzenie do testowania programu Microsoft Excel

Ten [wpis w blogu](/archive/blogs/gautamg/3-introducing-sample-excel-extension) zawiera link do [przykładowego rozszerzenia](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) dla struktury kodowanego testu interfejsu użytkownika. Możesz również wyświetlić całą [serię wpisów w blogu dla rozszerzalnych testów interfejsu użytkownika](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility).

> [!NOTE]
> Przykład jest przeznaczony do użycia z programem Microsoft Excel 2010. Może ona być niezgodna z innymi wersjami programu Excel.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)