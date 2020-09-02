---
title: 'Instrukcje: Edytowanie wartości rejestru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f0cd04b054d51119f6f6c1b0275c4f781656bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811939"
---
# <a name="how-to-edit-a-register-value"></a>Porady: edytowanie wartości rejestru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno rejestry jest dostępne tylko wtedy, gdy w oknie dialogowym **Opcje** jest **włączone debugowanie na** poziomie adresu.  
  
### <a name="to-change-the-value-of-a-register"></a>Aby zmienić wartość rejestru  
  
1. W oknie **rejestry** Użyj klawisza TAB lub myszy, aby przenieść punkt wstawiania do wartości, którą chcesz zmienić. Po rozpoczęciu wpisywania kursor musi znajdować się przed wartością, która ma zostać zastąpiona.  
  
2. Wpisz nową wartość.  
  
    > [!CAUTION]
    > Zmiana wartości rejestru (szczególnie w rejestrach EIP i EBP) może mieć wpływ na wykonywanie programu.  
  
    > [!CAUTION]
    > Edytowanie wartości zmiennoprzecinkowych może spowodować powstanie nieścisłych niedokładności z powodu konwersji dziesiętnej na binarną składników ułamkowych. Nawet pozornie niewielkiej ilości Edycja może spowodować zmianę niektórych najmniej znaczących bitów w rejestrze zmiennoprzecinkowym.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: korzystanie z okna rejestrów](../debugger/how-to-use-the-registers-window.md)
