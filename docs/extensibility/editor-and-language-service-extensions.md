---
title: Edytor i język usługi rozszerzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56c75eaca7ee97bf6ea33f3d0cce245599df5ca5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912510"
---
# <a name="editor-and-language-service-extensions"></a>Edytor i język rozszerzenia usługi
Możesz rozszerzyć większość funkcji edytora kodu Visual Studio. Edytor jest oparty na Windows Presentation Foundation (WPF) i są zapisywane w kodzie zarządzanym. Mimo że to różni się od projekty we wcześniejszych wersjach programu Visual Studio, zawiera większość tych samych funkcji. Aby rozszerzyć edytora, użyj Managed Extensibility Framework (MEF).

 Visual Studio SDK zawiera kart znanych jako *podkładki* do obsługi pakietów VSPackage, napisanych dla wcześniejszych wersji. Niemniej jednak w przypadku istniejącego pakietu VSPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|
|[Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)|Zawiera łącza do dokumentów, które prezentują projektu i funkcji edytora podstawowych i pokazują, jak rozszerzać go.|
|[Interfejsy starszej wersji w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)|Zawiera łącza do dokumentów, które wyjaśniają, jak uzyskać dostęp do podstawowy edytor z istniejącego kodu.|
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Zawiera łącza do dokumentów, które przedstawiają sposób tworzenia niestandardowych edytorów.|
|[Rozszerzalność usługi starszego języka](../extensibility/internals/legacy-language-service-extensibility.md)|Zawiera łącza do dokumentów, których opisano sposób integracji języków programowania w programie Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wprowadza struktura Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Wprowadza Windows Presentation Foundation (WPF).|