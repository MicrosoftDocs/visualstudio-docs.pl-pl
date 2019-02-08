---
title: Zabezpieczenia a zlokalizowane zestawy satelickie
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b33f890212cd3e310dc58a436b8674d20b81c453
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933122"
---
# <a name="security-and-localized-satellite-assemblies"></a>Zabezpieczenia a zlokalizowane zestawy satelickie

Jeśli zestaw głównych używa, silne nazwy, zestawy satelickie muszą być podpisane przy użyciu tego samego klucza prywatnego jako zestawu głównego. Jeśli klucz publiczny/prywatny, które pary jest niezgodny między głównym i zestawy satelickie, zasoby nie będą ładowane. Aby uzyskać więcej informacji na temat podpisywania zestawów, zobacz [jak: Podpisywanie zestawu silną nazwą](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

 Ogólnie rzecz biorąc może być konieczne podpisywania grupy w organizacji lub zewnętrznego organizacji podpisywania, zaloguj się przy użyciu klucza prywatnego. Jest to spowodowane wrażliwych klucza prywatnego: dostęp do często jest ograniczony do kilku osób. Możesz użyć opóźnionego podpisywania w czasie projektowania. Aby uzyskać więcej informacji, zobacz [opóźnienie podpisywania zestawu](/dotnet/framework/app-domains/delay-sign-assembly).

## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące zabezpieczeń zestawów](/dotnet/framework/app-domains/assembly-security-considerations)  - [podstawowe pojęcia dotyczące zabezpieczeń](/dotnet/standard/security/key-security-concepts)
- [Wprowadzenie do aplikacji międzynarodowych opartych na programie .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Lokalizowanie aplikacji](../ide/localizing-applications.md)
- [Globalizowanie i lokalizowanie aplikacji](../ide/globalizing-and-localizing-applications.md)