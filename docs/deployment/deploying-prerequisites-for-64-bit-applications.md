---
title: Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c70b58577f8aa6e391215658afb7f8fa43c9bb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928891"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych
Wdrożenie ClickOnce obsługuje instalację aplikacji na platformach 64-bitowych. Platformy docelowe są **x86** dla platform 32-bitowych **x64** obsługi zestawów instrukcji AMD64 oraz obsługą technologii EM64T maszyn i **Itanium** dla procesora Itanium 64-bitowych.

## <a name="prerequisites"></a>Wymagania wstępne
 Poniższa tabela zawiera listę pakietów redystrybucyjnych, używanego jako wymagania wstępne dotyczące instalacji aplikacji 64-bitowych.

 Jeśli wybierzesz wstępnie wymaganego składnika, który nie ma 64-bitowych składników, może zostać wyświetlony z ostrzeżeniem, że wybrane pakiety nie są dostępne dla platformy 64-bitowych.

| Pakiet redystrybucyjny | obsługuje x64 | Obsługa IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Yes | Nie |
| Biblioteki Visual C++ 2010 Runtime (IA64) | Nie | Yes |
| Biblioteki Visual C++ 2010 Runtime (x64) | Yes | Nie |
| Microsoft .NET Framework 4 (x86 i x64) | Tak | |
| Microsoft .NET Framework 4 Client Profile (x86 i x64) | Tak | |

## <a name="see-also"></a>Zobacz także
- [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)
- [Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [aplikacje 64-bitowe](/dotnet/framework/64-bit-apps)