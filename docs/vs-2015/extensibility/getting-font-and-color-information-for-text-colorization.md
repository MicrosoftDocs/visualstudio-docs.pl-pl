---
title: Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696854"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces służący do renderowania lub wyświetlania tekstu kolorowego w elementach interfejsu użytkownika (UI) zależy od typu projektu, jego technologii i preferencji deweloperskich. Na stronie właściwości **czcionki i kolory** są przechowywane ustawienia.  
  
 Większość implementacji, które wyświetlają tekst z kolorami, muszą mieć `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` skojarzone interfejsy do prezentowania, pobierania i przechowywania ustawień wyświetlania tekstu.  
  
> [!NOTE]
> W przypadku dostosowywania edytora podstawowego (który obsługuje **tekst EditorCategory**) zdecydowanie zaleca się używanie technologii kolorowania w usłudze językowej. Aby uzyskać więcej informacji, zobacz [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Pobieranie domyślnych informacji o czcionce i kolorach  
 Wszystkie ustawienia **czcionek i kolorów** dowolnego okna wyświetlającego tekst powinny być określone w **elementach wyświetlanych** jednej **kategorii**. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, Opcje — okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Aby kolorować, pakietu VSPackage musi uzyskać bieżące ustawienia **czcionek i kolorów** . Pakietu VSPackage można wykonać w następujący sposób, w zależności od potrzeb:  
  
- Użyj mechanizmu trwałości czcionki i koloru, aby pobrać stan przechowywany lub bieżący. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu usługi dostarczającego dane czcionek i kolorów, aby uzyskać wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , jeśli pakietu VSPackage nie jest również dostawcą czcionek i kolorów.  
  
- Zaimplementuj interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Aby upewnić się, że wyniki uzyskane przez sondowanie są aktualne, warto użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu w celu ustalenia, czy wymagana jest aktualizacja przed wywołaniem metod pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  
  
  Po uzyskaniu informacji o czcionce i kolorach Przeanalizuj tekst, który ma być wyświetlany, aby zidentyfikować elementy wymagające kolorowania, a następnie wyświetlić tekst w oknie przy użyciu odpowiednich czcionek i kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Używanie czcionek i tekstu](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Praca z kolorem](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (graficzny interfejs urządzenia)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
