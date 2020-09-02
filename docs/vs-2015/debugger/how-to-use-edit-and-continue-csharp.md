---
title: 'Instrukcje: korzystanie z edycji i kontynuowania (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807209"
---
# <a name="how-to-use-edit-and-continue-c"></a>Porady: korzystanie z opcji edytuj i kontynuuj (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą Edytuj i Kontynuuj dla języka C# można wprowadzać zmiany w kodzie w trybie przerwania podczas debugowania. Zmiany można zastosować bez konieczności zatrzymywania i ponownego uruchamiania sesji debugowania.  
  
 Funkcja Edytuj i Kontynuuj jest wywoływana automatycznie po wprowadzeniu zmian w trybie przerwania, a następnie wybraniu polecenia wykonania debugera, takiego jak **Kontynuuj**, **krok**lub **Ustaw następną instrukcję**lub Oceń funkcję w oknie debugera.  
  
> [!NOTE]
> Polecenie Edytuj i Kontynuuj nie jest obsługiwane podczas debugowania środowiska kompaktowego, zoptymalizowanego kodu, kodu natywnego/zarządzanego lub SQL Server kodu integracji środowiska uruchomieniowego języka wspólnego (CLR). Jeśli spróbujesz zastosować zmiany kodu w jednym z tych scenariuszy, debuger umieści okno dialogowe objaśniające, że edycja i kontynuacja nie są obsługiwane.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Aby wywoływać automatyczne edytowanie i kontynuowanie  
  
1. W trybie przerwania wprowadź zmiany w kodzie źródłowym.  
  
2. Z menu **Debuguj** kliknij polecenie **Kontynuuj**, **krok**lub **Ustaw następną instrukcję** lub Oceń funkcję w oknie debugera.  
  
     Nowy kod jest kompilowany, a debugowanie kontynuuje działanie nowego kodu. Niektóre zmiany nie są obsługiwane przez program Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć/wyłączyć funkcję Edytuj i Kontynuuj  
  
1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
2. W oknie dialogowym **Opcje** rozwiń węzeł **debugowanie** , a następnie wybierz pozycję **Edytuj i Kontynuuj**.  
  
3. W oknie dialogowym **Opcje** **Edytuj i Kontynuuj** zaznacz lub wyczyść pole wyboru **Włącz edytowanie i kontynuowanie** .  
  
     Ustawienie zacznie obowiązywać po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Obsługiwane zmiany kodu (C#)](../debugger/supported-code-changes-csharp.md)   
 [Edycja i kontynuowanie przy błędach i ostrzeżeniach (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
