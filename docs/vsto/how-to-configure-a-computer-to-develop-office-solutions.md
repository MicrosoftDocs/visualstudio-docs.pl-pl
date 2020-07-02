---
title: 'Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b13aa65e4dd5868a36e0dd833351b1d1751d8b0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546175"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Instrukcje: Konfigurowanie komputera do opracowywania rozwiązań pakietu Office
  Aby skonfigurować komputer deweloperski w taki sposób, aby można było użyć Microsoft Office narzędzia deweloperskie w programie Visual Studio, postępuj zgodnie z instrukcjami podanymi w tym temacie. Aby wykonać te kroki, musisz mieć uprawnienia administracyjne na komputerze deweloperskim.

### <a name="to-configure-the-development-computer"></a>Aby skonfigurować komputer deweloperski

1. Zainstaluj wersję programu Visual Studio, która zawiera narzędzia Office Developer Tools. Narzędzia Office Developer Tools są instalowane domyślnie. W przypadku dostosowania instalacji programu Visual Studio przez wybranie funkcji do zainstalowania upewnij się, że podczas instalacji wybrano opcję **Microsoft Office narzędzia deweloperskie** . Aby uzyskać więcej informacji na temat wersji programu Visual Studio, które obejmują narzędzia deweloperskie pakietu Office, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Zainstaluj wersję pakietu Office obsługiwaną przez narzędzia Office Developer Tools w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Upewnij się, że instalujesz także zestawów Pia dla zainstalowanej wersji pakietu Office. Zestawów PIA są domyślnie instalowane z pakietem Office. W przypadku modyfikowania Instalatora pakietu Office upewnij się, że dla aplikacji, które mają być używane, jest zaznaczona funkcja **Obsługa programowania .NET** .

3. Jeśli masz angielską wersję programu Visual Studio, ale używasz ustawień innych niż angielskie dla systemu Windows, możesz zainstalować [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pakiet językowy, aby zobaczyć [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] komunikaty w tym samym języku co system Windows. Wersje inne niż angielskie programu Visual Studio automatycznie instalują pakiet językowy. Pakiet językowy jest dostępny w [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Instrukcje: Instalowanie pakietu redystrybucyjnego środowiska uruchomieniowego Office Visual Studio Tools](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Instrukcje: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
