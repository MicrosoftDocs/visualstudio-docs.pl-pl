---
title: Rozszerzenia edytora i usługi językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712018"
---
# <a name="editor-and-language-service-extensions"></a>Rozszerzenia edytora i usługi językowej
Można rozszerzyć większość funkcji edytora kodu programu Visual Studio. Edytor jest oparty na Windows Presentation Foundation (WPF) i jest napisany w kodzie zarządzanym. Mimo że ten projekt różni się od projektów we wcześniejszych wersjach programu Visual Studio, zapewnia większość tych samych funkcji. Aby rozszerzyć edytor, należy użyć managed extensibility framework (MEF).

 Visual Studio SDK udostępnia karty znane jako *podkładki* do obsługi vsPackages, które zostały napisane dla wcześniejszych wersji. Niemniej jednak jeśli masz istniejący vsPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|
|[Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)|Łącza do dokumentów, które wprowadzają projekt i funkcje edytora podstawowego i pokazują, jak go rozszerzyć.|
|[Starsze interfejsy w edytorze](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Łącza do dokumentów, które wyjaśniają, jak uzyskać dostęp do edytora podstawowego z istniejącego kodu.|
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Łącza do dokumentów wyjaśniających sposób tworzenia edytorów niestandardowych.|
|[Rozszerzalność usługi języka starszego](../extensibility/internals/legacy-language-service-extensibility.md)|Łącza do dokumentów, które opisują sposób integracji języków programowania w programie Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wprowadza zarządzane ramy rozszerzalności (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Przedstawia Windows Presentation Foundation (WPF).|
