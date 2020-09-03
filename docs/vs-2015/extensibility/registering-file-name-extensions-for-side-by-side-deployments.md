---
title: Rejestrowanie rozszerzeń nazw plików dla wdrożeń równoległych | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163698"
---
# <a name="registering-file-name-extensions-for-side-by-side-deployments"></a>Rejestrowanie rozszerzeń nazw plików na potrzeby wdrożeń równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku pakietów VSPackage wdrożonych w środowisku Side-by-Side należy zarejestrować rozszerzenia nazw plików w celu kojarzenia plików z poprawną wersją programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Jeśli nie zostanie użyte rozszerzenie nazwy pliku specyficznego dla wersji, rejestracja umożliwia użytkownikom otwieranie plików projektu i elementów projektu w odpowiedniej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o rozszerzeniach nazw plików](../extensibility/about-file-name-extensions.md)  
 W tym artykule omówiono sposób rejestrowania rozszerzeń nazw plików.  
  
 [Określanie programów obsługi plików dla rozszerzeń nazw plików](../extensibility/specifying-file-handlers-for-file-name-extensions.md)  
 Zawiera informacje dotyczące sposobu rejestrowania aplikacji, które mogą otwierać, edytować i tak dalej, w przypadku konkretnego rozszerzenia nazwy pliku.  
  
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)  
 W tym artykule omówiono sposób rejestrowania zleceń.  
  
 [Zarządzanie równoległymi skojarzeniami plików](../extensibility/managing-side-by-side-file-associations.md)  
 W tym artykule omówiono sposób obsługi instalacji równoległych, w których należy wywołać konkretną wersję programu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Aby otworzyć plik.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)  
 W tym artykule opisano problemy związane z wieloma wersjami [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i pakietu VSPackage podczas opracowywania i wdrażania dla użytkowników końcowych.
