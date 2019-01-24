---
title: Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 96e5bc47a12e838fb11aa82c18981805abc4ae7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790786"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces, który renderuje lub wyświetla wyróżnione kolorem tekstu w elementach interfejsu użytkownika zależy od typu projektu, jego technologii i dla deweloperów preferencji. **Czcionki i kolory** strona właściwości są przechowywane ustawienia.  
  
 Większość implementacji, które są wyświetlane wyróżnione kolorem tekstu muszą `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` i skojarzone interfejsy, dla ustawienia wyświetlania prezentacji, pobieranie i przechowywanie tekstu.  
  
> [!NOTE]
>  Podczas dostosowywania podstawowy edytor (który obsługuje **EditorCategory tekstu**), zaleca się stosowania technologii kolorowanie w usługi języka. Aby uzyskać więcej informacji, zobacz [czcionkę i kolor Przegląd](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Uzyskiwanie domyślną czcionkę i kolor informacji  
 Wszystkie **czcionki i kolory** należy określić ustawienia okna wyświetlania tekstu w **Wyświetle elementy** jednego **kategorii**. Aby uzyskać więcej informacji, zobacz [czcionki i kolory, środowisko, opcje, okno dialogowe](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Kolorować, pakietu VSPackage musi uzyskać bieżące **czcionki i kolory** ustawienia. Pakietu VSPackage można to zrobić w następujący sposób, w zależności od jego potrzeb:  
  
- Użyj mechanizmu stanu trwałego czcionek i kolorów do pobrania przechowywanych lub bieżącego stanu. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do przechowywanych czcionkę i ustawienia kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu usługi dostarcza dane czcionek i kolorów, aby pobrać wystąpienie obiektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, jeśli pakietu VSPackage nie jest również dostawcy czcionek i kolorów.  
  
- Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.  
  
  Aby upewnić się, że wyniki uzyskane za pomocą sondowania znajdują się w górę do daty, warto użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do określenia, czy aktualizacja jest wymagana przed wywołaniem metody pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  
  
  Po użytkownik uzyskał informacje czcionek i kolorów, przeanalizować tekst, który ma być wyświetlany w celu oznaczenia elementów wymagających kolorowanie, a następnie wyświetlić tekst w oknie przy użyciu odpowiednich czcionek i kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Używanie czcionek i tekstu](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Praca z kolorem](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (graficzny interfejs urządzenia)](http://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
