---
title: Zabezpieczenia i zlokalizowane zestawy satelickie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672912"
---
# <a name="security-and-localized-satellite-assemblies"></a>Zabezpieczenia a zlokalizowane zestawy satelickie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli główny zestaw używa silnego nazewnictwa, zestawy satelickie muszą być podpisane przy użyciu tego samego klucza prywatnego co główny zestaw. Jeśli para kluczy publiczny/prywatny nie jest zgodna między zestawami głównymi i satelity, zasoby nie zostaną załadowane. Aby uzyskać więcej informacji o podpisywaniu zestawów, zobacz [How to: Sign a Assembly with silnej nazwy](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 Ogólnie rzecz biorąc, może być konieczne posiadanie grupy podpisywania lub rejestracji zewnętrznej organizacji podpisywania przy użyciu klucza prywatnego. Wynika to z poufnego charakteru klucza prywatnego: dostęp jest często ograniczony do kilku osób. Podczas opracowywania można użyć opóźnionego podpisywania. Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).

## <a name="see-also"></a>Zobacz też
 [Zagadnienia dotyczące zabezpieczeń zestawów](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) [kluczowe pojęcia dotyczące zabezpieczeń](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) [wprowadzenia do aplikacji międzynarodowych na podstawie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [lokalizowania](../ide/localizing-applications.md) aplikacji [globalizacji i lokalizowania](../ide/globalizing-and-localizing-applications.md) aplikacji
