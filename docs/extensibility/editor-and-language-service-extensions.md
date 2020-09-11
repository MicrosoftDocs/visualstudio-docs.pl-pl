---
title: Rozszerzenia edytora i usługi językowej | Microsoft Docs
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
ms.openlocfilehash: 71a38d6718c22419a0a61ffbab4fe2bf6fe6c552
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012441"
---
# <a name="editor-and-language-service-extensions"></a>Rozszerzenia edytora i usługi językowej
Można zwiększyć większość funkcji edytora kodu programu Visual Studio. Edytor jest oparty na Windows Presentation Foundation (WPF) i jest zapisywana w kodzie zarządzanym. Chociaż ten projekt różni się od projektów we wcześniejszych wersjach programu Visual Studio, zapewnia większość tych samych funkcji. Aby zwiększyć Edytor, użyj Managed Extensibility Framework (MEF).

 Zestaw Visual Studio SDK zawiera karty, które są nazywane *podkładkami* do obsługi pakietów VSPackage utworzonych dla wcześniejszych wersji. Jeśli jednak masz istniejący pakietu VSPackage, Zalecamy zaktualizowanie go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Tworzenie rozszerzenia z szablonem elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|
|[Poszerzanie edytora i usług językowych](../extensibility/extending-the-editor-and-language-services.md)|Łącza do dokumentów, które wprowadzają projekt i funkcje edytora podstawowego i pokazują, jak go zwiększyć.|
|[Starsze interfejsy w edytorze](../vs-2015/extensibility/legacy-interfaces-in-the-editor.md?view=vs-2015)|Linki do dokumentów, które wyjaśniają, jak uzyskać dostęp do podstawowego edytora z istniejącego kodu.|
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Linki do dokumentów objaśniających sposób tworzenia edytorów niestandardowych.|
|[Rozszerzalność starszej wersji usługi językowej](../extensibility/internals/legacy-language-service-extensibility.md)|Linki do dokumentów opisujących sposób integrowania języków programowania w programie Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Wprowadza Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Wprowadza Windows Presentation Foundation (WPF).|