---
title: 'Porady: używanie funkcji Edytuj i Kontynuuj (C#) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 4106a8bcaec8890192fdc33b9db0d66c12d8b07d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789171"
---
# <a name="how-to-use-edit-and-continue-c"></a>Porady: korzystanie z opcji edytuj i kontynuuj (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z funkcją Edytuj i Kontynuuj dla języka C# można wprowadzić zmiany do kodu w trybie przerwania podczas debugowania. Zmiany można stosować bez konieczności zatrzymania i ponownego uruchomienia sesji debugowania.  
  
 Edytuj i Kontynuuj jest wywoływane automatycznie, gdy możesz wprowadzać zmiany w trybie przerwania, a następnie wybierz wykonywania debugera polecenia, takie jak **Kontynuuj**, **kroku**, lub **Ustaw następną instrukcję**, lub oceń funkcję w oknie debugera.  
  
> [!NOTE]
>  Edytuj i Kontynuuj nie jest obsługiwane podczas debugowania platformy kompaktowej, zoptymalizowanego kodu mieszanego natywnego/zarządzanego lub kodu integracji środowiska uruchomieniowego (języka wspólnego CLR) wspólnego języka programu SQL Server. Jeśli spróbujesz zastosować zmiany kodu w jednym z tych scenariuszy, debuger wstawia się okno dialogowe wyjaśniające, że Edytuj i Kontynuuj nie jest obsługiwany.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>Aby wywołać Edytuj i Kontynuuj automatycznie  
  
1.  W trybie przerwy wprowadź zmiany do kodu źródłowego.  
  
2.  Z **debugowania** menu, kliknij przycisk **Kontynuuj**, **kroku**, lub **Ustaw następną instrukcję** lub oceń funkcję w oknie debugera.  
  
     Nowy kod jest skompilowany i debugowanie nadal stanowi nowy kod. Niektóre zmiany nie są obsługiwane przez Edytuj i Kontynuuj. Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu (C#)](../debugger/supported-code-changes-csharp.md).  
  
### <a name="to-enabledisable-edit-and-continue"></a>Aby włączyć lub wyłączyć Edytuj i Kontynuuj  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2.  W **opcje** okna dialogowego rozwiń **debugowanie** , a następnie wybierz węzeł **Edytuj i Kontynuuj**.  
  
3.  W **opcje** okno dialogowe **Edytuj i Kontynuuj** , zaznacz lub wyczyść **Włącz edytowanie i kontynuowanie** pole wyboru.  
  
     Ustawienie zostanie uwzględnione po ponownym uruchomieniu sesji debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj i Kontynuuj (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Obsługiwane zmiany kodu (C#)](../debugger/supported-code-changes-csharp.md)   
 [Edycja i kontynuowanie przy błędach i ostrzeżeniach (C#)](../misc/edit-and-continue-errors-and-warnings-csharp.md)



