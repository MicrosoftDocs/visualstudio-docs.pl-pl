---
title: Implementowanie niestandardowych kategorii i wyświetlanie elementów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 474d5c66507b56bea609568b6acfe9f5eff75e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64796837"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementowanie kategorii niestandardowych i elementów wyświetlanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietu VSPackage może zapewnić kontrolę nad czcionkami i kolorami tekstu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE) za pomocą niestandardowych kategorii i elementów wyświetlanych.  
  
 Kategorie niestandardowe i elementy wyświetlane znajdują się na stronie właściwości **czcionki i kolory** . Aby otworzyć stronę właściwości **czcionki i kolory** , w menu **Narzędzia** kliknij polecenie **Opcje**. Rozwiń węzeł **środowisko** , a następnie kliknij pozycję **czcionki i kolory**.  
  
 W przypadku korzystania z tego mechanizmu pakietów VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejs i powiązane z nim interfejsy.  
  
 W zasadzie ten mechanizm może służyć do modyfikowania wszystkich istniejących **elementów wyświetlanych** i **kategorii** , które je zawierają. Nie należy jednak używać go do modyfikacji **tekstu EditorCategory** lub jego **elementów wyświetlanych**. Aby uzyskać więcej informacji, zobacz [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md).  
  
 Aby zaimplementować niestandardowe **Kategorie** lub **elementy wyświetlane**, pakietu VSPackage musi:  
  
- Utwórz lub Zidentyfikuj kategorie w rejestrze.  
  
   Implementacja środowiska IDE na stronie właściwości **czcionki i kolory** używa tych informacji, aby prawidłowo wysyłać zapytania dotyczące usługi obsługującej daną kategorię.  
  
- Utwórz lub Zidentyfikuj grupy (opcjonalnie) w rejestrze.  
  
   Przydatne może być zdefiniowanie grupy, która reprezentuje Unię z co najmniej dwóch kategorii. W przypadku zdefiniowania grupy środowisko IDE automatycznie scala podkategorie i dystrybuuje wyświetlane elementy w grupie.  
  
- Implementowanie obsługi środowiska IDE.  
  
- Obsługuj zmiany czcionek i kolorów.  
  
  Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Aby utworzyć lub zidentyfikować kategorie  
  
- Konstruowanie specjalnego typu wpisu rejestru kategorii w sekcji [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ `<Category>` ]  
  
   *\<Category>* to niezlokalizowana nazwa kategorii.  
  
- Wypełnij rejestr dwiema wartościami:  
  
  |Nazwa|Typ|Dane|Opis|  
  |----------|----------|----------|-----------------|  
  |Kategoria|REG_SZ|GUID|Identyfikator GUID utworzony w celu zidentyfikowania kategorii.|  
  |Pakiet|REG_SZ|GUID|Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorię.|  
  
  Usługa określona w rejestrze musi dostarczyć implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> odpowiedniej kategorii.  
  
## <a name="to-create-or-identify-groups"></a>Aby utworzyć lub zidentyfikować grupy  
  
- Konstruowanie specjalnego typu wpisu rejestru kategorii w sekcji [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<group>* ]  
  
   *\<group>* to nie jest zlokalizowana nazwa grupy.  
  
- Wypełnij rejestr dwiema wartościami:  
  
  |Nazwa|Typ|Dane|Opis|  
  |----------|----------|----------|-----------------|  
  |Kategoria|REG_SZ|GUID|Identyfikator GUID utworzony w celu zidentyfikowania grupy.|  
  |Pakiet|REG_SZ|GUID|Identyfikator GUID usługi, która obsługuje kategorię.|  
  
  Usługa określona w rejestrze musi dostarczyć implementację `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` dla odpowiedniej grupy.  
  
## <a name="to-implement-ide-support"></a>Aby zaimplementować obsługę środowiska IDE  
  
- Implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A> , która zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejs lub `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfejs IDE dla każdego dostarczonego identyfikatora GUID **kategorii** lub grupy.  
  
- Dla każdej **kategorii** , która obsługuje, pakietu VSPackage implementuje oddzielne wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu.  
  
- Metody implementowane za pomocą programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> muszą zapewnić IDE z:  
  
  - Listy **elementów wyświetlanych** w **kategorii.**  
  
  - Lokalizowalne nazwy dla **elementów wyświetlanych**.  
  
  - Wyświetl informacje dla każdego elementu członkowskiego **kategorii**.  
  
  > [!NOTE]
  > Każda **Kategoria** musi zawierać co najmniej jeden **element wyświetlany**.  
  
- IDE używa `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfejsu do definiowania Unii kilku kategorii.  
  
   Jego implementacja zapewnia środowisko IDE z:  
  
  - Lista **kategorii** , które składają się na daną grupę.  
  
  - Dostęp do wystąpień <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> obsługujących każdą **kategorię** w grupie.  
  
  - Lokalizowalne nazwy grup.  
  
- Aktualizowanie środowiska IDE:  
  
   IDE buforuje informacje o ustawieniach **czcionek i kolorów** . W związku z tym po zmianie konfiguracji **czcionki i koloru** IDE zaleca się upewnienie się, że pamięć podręczna jest aktualna.  
  
  Aktualizowanie pamięci podręcznej odbywa się za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu i może być wykonywane globalnie lub tylko dla wybranych elementów.  
  
## <a name="to-handle-font-and-color-changes"></a>Aby obsłużyć zmiany czcionki i koloru  
 Aby prawidłowo obsługiwać Kolorowanie tekstu wyświetlanego przez pakietu VSPackage, usługa kolorowania obsługująca pakietu VSPackage musi odpowiadać na zmiany zainicjowane przez użytkownika za pomocą strony właściwości **czcionki i kolory** . Pakietu VSPackage wykonuje to przez:  
  
- Obsługa zdarzeń generowanych przez środowisko IDE przez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.  
  
     IDE wywołuje odpowiednią metodę po zmodyfikowaniu przez użytkownika strony **czcionki i kolory** . Na przykład wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metodę w przypadku wybrania nowej czcionki.  
  
     -lub-  
  
- Sondowanie środowiska IDE pod kątem zmian.  
  
     Można to zrobić za pomocą interfejsu zaimplementowanego przez system <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> . Chociaż głównie do obsługi trwałości, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Metoda może służyć do uzyskiwania informacji o czcionce i kolorach dla **elementów wyświetlanych**. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    > Aby upewnić się, że wyniki uzyskane przez sondowanie są poprawne, przydatne może być użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejsu w celu ustalenia, czy opróżnianie pamięci podręcznej i aktualizacja jest konieczna przed wywołaniem metod pobierania <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Uzyskiwanie informacji o czcionkach i kolorach na potrzeby kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Uzyskiwanie dostępu do przechowywanych ustawień czcionek i kolorów](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Instrukcje: uzyskiwanie dostępu do wbudowanych czcionek i schematu kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)
