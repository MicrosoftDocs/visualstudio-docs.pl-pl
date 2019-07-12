---
title: Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing stored settings
- font and color control [Visual Studio SDK], persistence
- colors, accessing stored settings
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fbb2f118d903eae2124e705f14c7aa7b51bf9c4d
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821831"
---
# <a name="accessing-stored-font-and-color-settings"></a>Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Zintegrowanego środowiska programistycznego (IDE) przechowuje zmodyfikowane ustawienia czcionek i kolorów w rejestrze. Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu uzyskać dostępu do tych ustawień.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Aby zainicjować stanu trwałości czcionki i kolory  
 Informacje o czcionek i kolorów są przechowywane według kategorii w następującej lokalizacji rejestru: [HKCU\SOFTWARE\Microsoft \Visual Studio\\ *\<wersji programu Visual Studio >* \FontAndColors\\  *\<CategoryGUID >* ], gdzie  *\<CategoryGUID >* to kategoria identyfikatora GUID.  
  
 W związku z tym aby zainicjować trwałości, pakietu VSPackage musi:  
  
- Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu, wywołując `QueryService` względem dostawcy usługi global service.  
  
     `QueryService` musi zostać wywołana przy użyciu argumentu identyfikator usługi z `SID_SVsFontAndColorStorage` i argument identyfikator interfejsu `IID_IVsFontAndColorStorage`.  
  
- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodę, aby otworzyć kategorii w celu jego utrwalenia przy użyciu identyfikatora GUID danej kategorii i flagi trybu jako argumenty.  
  
  Tryb, określony przez `fFlags` argument, jest tworzony z wartości w <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> wyliczenia. W tym trybie kontrolki:  

  - Ustawienia, które mogą być udostępniane za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  

  - Wszystkie ustawienia lub tylko te, które zmodyfikować użytkowników i które można odzyskać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  

  - Sposób propagowanie zmian ustawień użytkownika.  

  - Format wartości kolorów, które są używane.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Aby używać stanu trwałości czcionki i kolory  
 Utrwalanie czcionki i kolory obejmuje:  
  
- Synchronizacja ustawień środowiska IDE, za pomocą ustawień przechowywanych w rejestrze.  
  
- Propagowanie informacji modyfikacji rejestru.  
  
- Ustawianie i pobieranie ustawień przechowywanych w rejestrze.  
  
  Synchronizacja ustawień magazynu z ustawieniami środowiska IDE jest dużej mierze przejrzyste. Podstawowy IDE automatycznie zapisuje zaktualizowanych ustawień dla **Wyświetle elementy** wpisów rejestru kategorii.  
  
  Jeśli wiele pakietów VSPackage mają określoną kategorię, pakietu VSPackage powinny wymagać generowane są zdarzenia podczas metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu służą do modyfikowania ustawień rejestru przechowywanych.  
  
  Generowanie zdarzeń nie jest włączona domyślnie. Aby włączyć generowanie zdarzeń, kategorii muszą być otwarte przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. Powoduje to, że środowisko IDE do wywołania odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metody, która implementuje pakietu VSPackage.  
  
> [!NOTE]
> Modyfikacje za pośrednictwem **czcionek i kolorów** stronie właściwości generowanie zdarzeń niezależnie od <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. Możesz użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu, aby ustalić, czy aktualizację pamięci podręcznej ustawienia czcionek i kolorów jest wymagana przed wywołaniem metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> klasy.  
  
### <a name="storing-and-retrieving-information"></a>Przechowywanie i pobieranie informacji  
 Uzyskać lub skonfigurować informacje, które użytkownik może modyfikować dla nazwanego wyświetlanego elementu w kategorii otwarte, wywołaj pakietów VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody.  
  
 Informacje o czcionki atrybuty dla określonej kategorii są uzyskiwane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metody.  
  
> [!NOTE]
> `fFlags` Argument, który jest przekazywany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metody w momencie otwarcia tej kategorii definiuje zachowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody. Domyślnie te metody zwrócić tylko informacje aboutdisplay itemsthat uległy zmianie. Jednak jeśli kategoria jest otwarty za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> Flaga zarówno zaktualizowane i Wyświetl niezmienione elementy może zostać oceniony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Domyślnie tylko zmienione **Wyświetle elementy** informacje są przechowywane w rejestrze. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Interfejsu nie może służyć do pobierania wszystkich ustawień czcionek i kolorów.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metody zwracają REGDB_E_KEYMISSING, (0x80040152L) możesz użyć do pobrania informacji o zmianie **Wyświetle elementy**.  
  
 Ustawienia wszystkich **Wyświetle elementy** w szczególności **kategorii** można uzyskać za pomocą metody `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementowanie kategorii niestandardowych i elementów wyświetlanych](../extensibility/implementing-custom-categories-and-display-items.md)
