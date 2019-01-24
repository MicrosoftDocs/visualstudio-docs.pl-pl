---
title: Rozszerzone diagramy warstw | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-devops-techdebt
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 28712373b527f2605c47e9038ed169f0217636bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796808"
---
# <a name="extend-layer-diagrams"></a>Rozszerzone diagramy warstw
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, do tworzenia i aktualizowania diagramy warstwowe, a do sprawdzania poprawności strukturę kodu programu względem diagramów warstwowych w Visual Studio. Możesz dodać polecenia, które są wyświetlane w menu skrótów (kontekstu), diagramy Dostosowywanie gestów przeciągania i upuszczania oraz dostęp do warstwy modelu z poziomu szablonów tekstu. Można spakować te rozszerzenia w Visual Studio Integration rozszerzenie (VSIX) i rozdystrybuować je innym użytkownikom programu Visual Studio.  
  
 Aby uzyskać więcej informacji o diagramach warstwowych zobacz:  
  
-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)  
  
-   [Diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)  
  
-   [Tworzenie diagramów warstw z kodu](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="prereqs"></a> Wymagania  
 Musisz mieć zainstalowane na komputerze, gdzie chcesz rozwijać swoje rozszerzenia warstwy następujące elementy:  
  
- Visual Studio  
  
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
- [Modeling SDK for Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148)  
  
  Konieczne jest posiadanie odpowiedniej wersji programu Visual Studio zainstalowany na komputerze, na którym chcesz uruchomić swoje rozszerzenia warstwy. Aby uzyskać więcej informacji, zobacz [wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md).  
  
  Aby dowiedzieć się, które wersje programu Visual Studio obsługują diagramy warstwowe, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie poleceń i gestów do diagramów warstw](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Dodawanie niestandardowej walidacji architektury do diagramów warstw](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Dodawanie właściwości niestandardowych do diagramów warstw](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Nawigowanie i aktualizowanie modeli warstw w kodzie programu](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Wdrażanie rozszerzenia modelu warstwy](../modeling/deploy-a-layer-model-extension.md)  
  
 [Rozwiązywanie problemów z rozszerzeniami dla diagramów warstw](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)   
 [Diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)   
 [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)   
 [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)   
 [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md)   
 [Otwieranie modelu UML za pomocą interfejsu API programu Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
