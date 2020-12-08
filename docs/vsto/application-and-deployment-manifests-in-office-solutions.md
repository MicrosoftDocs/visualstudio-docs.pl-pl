---
title: Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office
description: Dowiedz się, w jaki sposób manifest aplikacji jest plikiem XML, który zawiera informacje, które są używane przez rozwiązanie pakietu Office do lokalizowania i aktualizowania zestawów.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ca8cf2774b7a24ec3bef40418b6a2157bf0f992
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844715"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Aplikacje i manifesty wdrożenia w rozwiązaniach pakietu Office
  Manifest aplikacji to plik XML, który zawiera informacje, które są używane przez rozwiązanie pakietu Office do lokalizowania i aktualizowania zestawów. Manifest aplikacji może być używany z manifestem wdrożenia, który jest plikiem XML przechowywanym na serwerze, który zawiera informacje konieczne do zlokalizowania najnowszej wersji manifestu aplikacji i zestawów.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Struktura manifestu dla rozwiązań pakietu Office
 W przypadku rozwiązań Microsoft Office utworzonych przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio wszystkie manifesty są oparte na standardowym schemacie technologii ClickOnce. Podczas wdrażania rozwiązań pakietu Office manifesty aplikacji dla projektów dodatków na poziomie dokumentu i VSTO znajdują się w pamięci podręcznej ClickOnce. Manifesty wdrożenia nie są kopiowane na komputer kliencki.

 Aby uzyskać informacje o zawartości manifestów aplikacji i wdrażania dla projektów pakietu Office, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md) i [manifestów wdrażania dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Tworzenie manifestów aplikacji i wdrażania
 Manifesty aplikacji są tworzone automatycznie w ramach procesu kompilacji. Za każdym razem, gdy kompilujesz projekt na poziomie dokumentu, lokalizacja manifestu wdrożenia jest osadzona w dokumencie jako właściwość dokumentu niestandardowego. W przypadku dodatków narzędzi VSTO lokalizacja manifestu wdrożenia jest przechowywana w rejestrze.

 Aby uzyskać więcej informacji na temat **Kreatora publikacji**, zobacz [wdrażanie rozwiązania z pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Aby uzyskać więcej informacji na temat sposobu działania manifestów z rozwiązaniami pakietu Office, zobacz [wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także

- [Architektura dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [Manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md)