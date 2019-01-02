---
title: Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 24650d2cb4cbed3a5b4c4f1ee02e395e7b8c2988
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828564"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office
  Manifest aplikacji jest plikiem XML, który dostarcza informacje o używanym przez rozwiązania do pakietu Office, aby znaleźć i zaktualizować jego zestawów. Manifest aplikacji może służyć z manifestu wdrażania jest plikiem XML przechowywane na serwerze, który zawiera informacje potrzebne do zlokalizowania aktualna wersja manifestu aplikacji i zestawy.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Struktura manifestu dla rozwiązań pakietu Office
 Rozwiązania Microsoft Office utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio wszystkie manifesty opierają się na schemat standardowy ClickOnce. Podczas wdrażania rozwiązania pakietu Office, manifestów aplikacji na poziomie dokumentu i projektów dodatku VSTO znajdują się w pamięci podręcznej funkcji ClickOnce. Manifesty wdrożenia nie są kopiowane do komputera klienckiego.

 Aby uzyskać informacje o zawartości aplikacji i manifestów wdrożenia dla projektów pakietu Office, zobacz [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md) i [manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Tworzenie aplikacji i wdrażania manifestów
 Manifesty aplikacji są tworzone automatycznie jako część procesu kompilacji. Za każdym razem, gdy tworzysz projekt poziomie dokumentu, lokalizację pliku manifestu wdrożenia zostanie osadzony w dokumencie niestandardową właściwość dokumentu. Dla dodatków narzędzi VSTO dla programów lokalizację pliku manifestu wdrożenia są przechowywane w rejestrze.

 Aby uzyskać więcej informacji na temat **Kreatora publikacji**, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 Aby uzyskać więcej informacji na temat manifestów współpracują z rozwiązań pakietu Office, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także

- [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [Manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md)