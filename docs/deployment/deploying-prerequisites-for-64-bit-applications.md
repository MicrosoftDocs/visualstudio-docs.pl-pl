---
title: Wdrażanie wymagań wstępnych dla aplikacji 64-bitowych | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928891"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Wdrażanie wstępnie wymaganych składników dla aplikacji 64-bitowych
Wdrożenie ClickOnce obsługuje instalację aplikacji na platformach 64-bitowych. Platformy docelowe to **x86** dla platform 32-bitowych, **x64** dla maszyn obsługujących zestawy instrukcji amd64 i EM64T oraz **procesor Itanium** dla 64-bitowego procesora Itanium.

## <a name="prerequisites"></a>Wymagania wstępne
 W poniższej tabeli wymieniono pakiety redystrybucyjne, których można użyć jako wymagań wstępnych instalacji aplikacji 64-bitowej.

 W przypadku wybrania wymagań wstępnych, które nie mają składników 64-bitowych, może pojawić się ostrzeżenie z informacją o tym, że wybrane pakiety nie są dostępne dla platformy 64-bitowej.

| Pakiet redystrybucyjny | Obsługa systemu x64 | Obsługa IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Tak | Nie |
| Biblioteki środowiska uruchomieniowego Visual C++ 2010 (IA64) | Nie | Tak |
| Biblioteki środowiska uruchomieniowego Visual C++ 2010 (x64) | Tak | Nie |
| Microsoft .NET Framework 4 (x86 i x64) | Tak | |
| Profil klienta Microsoft .NET Framework 4 (x86 i x64) | Tak | |

## <a name="see-also"></a>Zobacz też
- [Wdrażanie aplikacji, usług i składników](../deployment/deploying-applications-services-and-components.md)
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64-bitowe aplikacje](/dotnet/framework/64-bit-apps)