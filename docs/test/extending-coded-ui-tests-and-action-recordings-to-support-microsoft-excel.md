---
title: Poszerzenie kodowanych testów interfejsu użytkownika i nagrań akcji
description: Dowiedz się, jak utworzyć rozszerzenie dla struktury kodowanego testu interfejsu użytkownika dla określonego interfejsu użytkownika, wykorzystując rozszerzalność kodowanego środowiska testowania interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 8c4a846fe9425af7dc62ef93276c0272f480b7f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949873"
---
# <a name="extend-coded-ui-tests-and-action-recordings"></a>Poszerzenie kodowanych testów interfejsu użytkownika i nagrań akcji

Struktura testowania dla kodowanych testów interfejsu użytkownika i nagrań akcji nie obsługuje każdego możliwego interfejsu użytkownika. Może nie obsługiwać określonego interfejsu użytkownika, który ma zostać przetestowany. Na przykład nie można natychmiast utworzyć kodowanego testu interfejsu użytkownika lub rejestrowania akcji dla arkusza kalkulacyjnego programu Microsoft Excel. Można jednak utworzyć własne rozszerzenie dla struktury kodowanego testu interfejsu użytkownika, która obsługuje określony interfejs użytkownika, wykorzystując rozszerzalność kodowanego środowiska testowania interfejsu użytkownika.

![Architektura testu interfejsu użytkownika](../test/media/ui_testarch.png)

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="sample-extension-to-test-microsoft-excel"></a>Przykładowe rozszerzenie do testowania programu Microsoft Excel

Ten [wpis w blogu](/archive/blogs/gautamg/3-introducing-sample-excel-extension) zawiera link do [przykładowego rozszerzenia](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Components.PostAttachments/00/09/94/38/24/ExcelPluginSample.zip) dla struktury kodowanego testu interfejsu użytkownika. Możesz również wyświetlić całą [serię wpisów w blogu dla rozszerzalnych testów interfejsu użytkownika](/archive/blogs/gautamg/series-on-coded-ui-test-extensibility).

> [!NOTE]
> Przykład jest przeznaczony do użycia z programem Microsoft Excel 2010. Może ona być niezgodna z innymi wersjami programu Excel.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110))
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika](../test/best-practices-for-coded-ui-tests.md)
- [Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)