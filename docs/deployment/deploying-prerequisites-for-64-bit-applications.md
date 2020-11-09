---
title: Wdrażanie wymagań wstępnych dla aplikacji 64-bitowych | Microsoft Docs
description: Informacje o pakietach redystrybucyjnych, których można użyć jako wymagań wstępnych dla wdrażania aplikacji ClickOnce na platformach 64-bitowych.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c051e57bb6af707e7bd5c096e230966e98498bd2
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382913"
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