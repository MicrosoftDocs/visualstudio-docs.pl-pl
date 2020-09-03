---
title: Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821831"
---
# <a name="accessing-stored-font-and-color-settings"></a>Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Zintegrowane środowisko programistyczne (IDE) przechowuje zmodyfikowane ustawienia czcionek i kolorów w rejestrze. Możesz użyć interfejsu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Aby uzyskać dostęp do tych ustawień.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Aby zainicjować trwałość stanu czcionek i kolorów  
 Informacje o czcionkach i kolorach są przechowywane według kategorii w następującej lokalizacji rejestru: [HKCU\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<CategoryGUID>* ], gdzie *\<CategoryGUID>* jest identyfikatorem GUID kategorii.  
  
 W związku z tym, aby zainicjować trwałość, pakietu VSPackage musi:  
  
- Uzyskaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejs, wywołując `QueryService` do globalnego dostawcę usług.  
  
     `QueryService` musi być wywoływana przy użyciu argumentu identyfikatora usługi `SID_SVsFontAndColorStorage` i ARGUMENTU identyfikatora interfejsu `IID_IVsFontAndColorStorage` .  
  
- Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metody, aby otworzyć kategorię, która ma być utrwalona przy użyciu identyfikatora GUID kategorii i flagi Mode jako argumenty.  
  
  Tryb określony przez `fFlags` argument jest zbudowany z wartości w <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> wyliczeniu. Ten tryb kontroluje:  

  - Ustawienia, do których można uzyskać dostęp za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  

  - Wszystkie ustawienia lub tylko te, które są modyfikowane przez użytkowników i są przez ten <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejs.  

  - Sposób propagowania zmian w ustawieniach użytkownika.  

  - Format wartości kolorów, które są używane.  

## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Aby użyć trwałości stanu czcionek i kolorów  
 Czcionki i kolory utrwalające są następujące:  
  
- Synchronizowanie ustawień środowiska IDE z ustawieniami przechowywanymi w rejestrze.  
  
- Propagowanie informacji o modyfikacji rejestru.  
  
- Ustawianie i pobieranie ustawień przechowywanych w rejestrze.  
  
  Synchronizowanie ustawienia magazynu z ustawieniami IDE jest w dużym stopniu przezroczyste. Bazowe środowisko IDE automatycznie zapisuje zaktualizowane ustawienia dla **elementów wyświetlanych** do wpisów rejestru kategorii.  
  
  Jeśli wiele pakietów VSPackage ma określoną kategorię, pakietu VSPackage powinien wymagać generowania zdarzeń, gdy metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu są używane do modyfikowania przechowywanych ustawień rejestru.  
  
  Domyślnie generowanie zdarzeń nie jest włączone. Aby włączyć generowanie zdarzeń, należy otworzyć kategorię przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> . Powoduje to wywołanie przez środowisko IDE odpowiedniej <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metody, która implementuje pakietu VSPackage.  
  
> [!NOTE]
> Modyfikacje na stronie właściwości **czcionki i koloru** generują zdarzenia niezależne od <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Można użyć interfejsu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Aby określić, czy przed wywołaniem metod klasy należy zaktualizować ustawienia czcionek i kolorów w pamięci podręcznej <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> .  
  
### <a name="storing-and-retrieving-information"></a>Przechowywanie i pobieranie informacji  
 Aby uzyskać lub skonfigurować informacje, które użytkownik może modyfikować dla nazwanego elementu wyświetlanego w otwartej kategorii, pakietów VSPackage wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metody i.  
  
 Informacje o atrybutach czcionki dla określonej kategorii są uzyskiwane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metod i.  
  
> [!NOTE]
> `fFlags`Argument, który jest przesyłany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metody, gdy ta kategoria została otwarta definiuje zachowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metod i. Domyślnie te metody zwracają tylko informacje aboutdisplay itemsthat, które uległy zmianie. Jednakże jeśli kategoria jest otwierana przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> flagi, dostęp do elementów wyświetlanych zarówno zaktualizowanych, jak i niezmienionych jest możliwy dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> .  
  
 Domyślnie tylko zmienione informacje o **elementach wyświetlanych** są przechowywane w rejestrze. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>Nie można użyć interfejsu do pobrania wszystkich ustawień czcionek i kolorów.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> Metody i zwracają REGDB_E_KEYMISSING, (0x80040152L), gdy są używane do pobierania informacji o niezmienionych **elementach wyświetlanych**.  
  
 Ustawienia wszystkich **wyświetlanych elementów** w określonej **kategorii** można uzyskać przy użyciu metod `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementowanie kategorii niestandardowych i elementów wyświetlanych](../extensibility/implementing-custom-categories-and-display-items.md)
