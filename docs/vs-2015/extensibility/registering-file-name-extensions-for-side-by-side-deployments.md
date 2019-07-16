---
title: Rejestrowanie rozszerzeń nazw plików dla wdrożeń Side-By-Side | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 354b91dd1282df9726c1ee9c47f610b0dfdd9c1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163698"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wdrożony w środowisku side-by-side pakietów VSPackage, musisz się zarejestrować, rozszerzenia nazw plików, aby skojarzyć pliki z poprawną wersję [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jeśli nie używasz rozszerzenia nazwy pliku określonej wersji, rejestracji umożliwia użytkownikom Otwórz swój projekt i projektu pliki elementu w odpowiedniej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md)  
 W tym artykule omówiono, jak zarejestrowanych rozszerzeń nazw plików.  
  
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Zawiera informacje o sposobie rejestrowania aplikacji, które można otworzyć, edycji i tak dalej, rozszerzenie nazwy pliku określonej.  
  
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)  
 W tym artykule omówiono sposób rejestrowania zleceń.  
  
 [Zarządzanie równoległymi skojarzeniami plików](../extensibility/managing-side-by-side-file-associations.md)  
 W tym artykule omówiono sposób obsługi instalacje side-by-side, w którym konkretnej wersji [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] powinny być używane w celu otwarcia pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 W tym artykule opisano problemy związane z wieloma wersjami [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i usługi pakietu VSPackage podczas procesu projektowania i wdrażania dla użytkowników końcowych.
