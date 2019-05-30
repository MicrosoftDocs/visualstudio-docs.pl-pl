---
title: Edytor i język usługi rozszerzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1df6f65db70425650fc2860bf5ddf6e2d2e203c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353381"
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