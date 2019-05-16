---
title: 'Instrukcje: Dodawanie zależności do pakietu VSIX | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697508"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Instrukcje: Dodawanie zależności do pakietu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować wdrożenie pakietu VSIX, które instaluje wszystkie zależności, które nie są już obecne na komputerze docelowym. Aby to osiągnąć, należy uwzględnić zależności VSIX, aby plik source.extension.vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Aby dodać zależności  
  
1. Otwórz plik source.extension.vsixmanifest w **projektowania** widoku. Przejdź do **zależności** kartę, a następnie kliknij przycisk **New**.  
  
2. Aby dodać zainstalowane rozszerzenie: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **zainstalowane rozszerzenie** a następnie w **nazwa**, zaznacz rozszerzenie, na liście.  
  
3. Aby dodać inny VSIX, który nie jest zainstalowany:: w **Dodawanie nowych zależności** okno dialogowe, wybierz opcję **plików w systemie plików** , a następnie użyj **Przeglądaj** przycisk, aby wybrać VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu 1.0 rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
