---
title: Zabezpieczenia a zlokalizowane zestawy satelickie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c810c6c7e0c0c73557e6b38860c1e6d3953b225
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691285"
---
# <a name="security-and-localized-satellite-assemblies"></a>Zabezpieczenia a zlokalizowane zestawy satelickie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli zestaw głównych używa, silne nazwy, zestawy satelickie muszą być podpisane przy użyciu tego samego klucza prywatnego jako zestawu głównego. Jeśli klucz publiczny/prywatny, które pary jest niezgodny między głównym i zestawy satelickie, zasoby nie będą ładowane. Aby uzyskać więcej informacji na temat podpisywania zestawów, zobacz [jak: Podpisywanie zestawu silną nazwą](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Ogólnie rzecz biorąc może być konieczne podpisywania grupy w organizacji lub zewnętrznego organizacji podpisywania, zaloguj się przy użyciu klucza prywatnego. Jest to spowodowane wrażliwych klucza prywatnego: dostęp do często jest ograniczony do kilku osób. Możesz użyć opóźnionego podpisywania w czasie projektowania. Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące zabezpieczeń zestawów](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Główne pojęcia dotyczące zabezpieczeń](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Lokalizowanie aplikacji](../ide/localizing-applications.md)   
 [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)
