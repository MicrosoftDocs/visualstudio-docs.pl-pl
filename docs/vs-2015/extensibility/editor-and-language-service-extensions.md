---
title: Edytor i język usługi rozszerzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b5e0b568cee873d29f73eb2b81e38d49b76b5844
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778764"
---
# <a name="editor-and-language-service-extensions"></a>Rozszerzenia edytora i usługi językowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz rozszerzyć większość funkcji edytora kodu Visual Studio. Edytor jest oparty na Windows Presentation Foundation (WPF) i są zapisywane w kodzie zarządzanym. Mimo że to różni się od projekty we wcześniejszych wersjach programu Visual Studio, zawiera większość tych samych funkcji. Aby rozszerzyć edytora, użyj Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK zawiera kart znanych jako *podkładki* do obsługi pakietów VSPackage, napisanych dla wcześniejszych wersji. Niemniej jednak w przypadku istniejącego pakietu VSPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Tworzenie rozszerzenia za pomocą szablonu elementu edytora](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Wprowadzenie do korzystania z szablonów elementów edytora.|  
|[Rozszerzanie usług edytora i języka](../extensibility/extending-the-editor-and-language-services.md)|Zawiera łącza do dokumentów, które prezentują projektu i funkcji edytora podstawowych i pokazują, jak rozszerzać go.|  
|[Starsze interfejsy w edytorze](../extensibility/legacy-interfaces-in-the-editor.md)|Zawiera łącza do dokumentów, które wyjaśniają, jak uzyskać dostęp do podstawowy edytor z istniejącego kodu.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Zawiera łącza do dokumentów, które przedstawiają sposób tworzenia niestandardowych edytorów.|  
|[Rozszerzalność starszej wersji usługi językowej](../extensibility/internals/legacy-language-service-extensibility.md)|Zawiera łącza do dokumentów, których opisano sposób integracji języków programowania w programie Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Wprowadza struktura Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Wprowadza Windows Presentation Foundation (WPF).|

