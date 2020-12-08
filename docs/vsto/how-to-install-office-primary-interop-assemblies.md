---
title: 'Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office'
description: Dowiedz się, jak zainstalować Microsoft Office podstawowych zestawów międzyoperacyjnych (zestawów PIA) podczas instalacji pakietu Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15a55650f2e4a434343c9128cc8f28117b54288e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845885"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office
  Zainstaluj Microsoft Office podstawowych zestawów międzyoperacyjnych (zestawów PIA) podczas instalacji pakietu Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Aby zainstalować zestawów Pia podczas instalowania pakietu Office

1. Upewnij się, że masz wersję .NET Framework, która nie jest starsza niż 2,0.

2. Zainstaluj Microsoft Office i upewnij się, że dla aplikacji, które mają zostać rozszerzone, została wybrana funkcja **obsługi programowania .NET** (Ta funkcja jest uwzględniona w instalacji domyślnej).

    > [!WARNING]
    > Domyślnie narzędzie PIA jest osadzane w rozwiązaniu podczas jego kompilowania, aby nie trzeba było rozpowszechniać zestawów Pia do użytkowników jako wymaganie wstępne do korzystania z dodatku narzędzi VSTO lub dostosowywania.

## <a name="see-also"></a>Zobacz także
- [Podstawowe zestawy międzyoperacyjności pakietu Office](../vsto/office-primary-interop-assemblies.md)
- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Instrukcje: Instalowanie pakietu redystrybucyjnego środowiska uruchomieniowego Office Visual Studio Tools](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
