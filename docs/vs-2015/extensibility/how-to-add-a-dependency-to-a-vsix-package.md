---
title: 'Instrukcje: Dodawanie zależności do pakietu VSIX | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697508"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Instrukcje: dodawanie zależności do pakietu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można skonfigurować wdrożenie pakietu VSIX, które instaluje wszystkie zależności, które nie znajdują się jeszcze na komputerze docelowym. Aby to osiągnąć, Uwzględnij zależności VSIX do pliku source. Extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Aby dodać zależność  
  
1. Otwórz plik source. Extension. vsixmanifest w widoku **projektu** . Przejdź do karty **zależności** i kliknij pozycję **Nowy**.  
  
2. Aby dodać zainstalowane rozszerzenie: w oknie dialogowym **Dodaj nową zależność** wybierz **zainstalowane rozszerzenie** , a następnie w polu **Nazwa**wybierz rozszerzenie na liście.  
  
3. Aby dodać inny VSIX, który nie jest zainstalowany:: w oknie dialogowym **Dodaj nową zależność** wybierz pozycję **plik w systemie plików** , a następnie użyj przycisku **Przeglądaj** , aby wybrać VSIX.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja schematu rozszerzenia VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
