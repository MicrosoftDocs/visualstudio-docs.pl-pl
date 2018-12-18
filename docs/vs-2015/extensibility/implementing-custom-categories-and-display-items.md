---
title: Implementowanie niestandardowych kategorii i wyświetlenie elementów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 394f8f99539ab49c1201fa61ce612aee22ff2064
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769109"
---
# <a name="implementing-custom-categories-and-display-items"></a>Implementowanie niestandardowych kategorii i wyświetlenie elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietu VSPackage może zapewnić kontrolę nad czcionek i kolorów tekstu do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) za pomocą niestandardowych kategorii i wyświetlenie elementów.  
  
 Niestandardowe kategorie i wyświetle elementy znajdują się na **czcionki i kolory** stronę właściwości. Aby otworzyć **czcionki i kolory** na stronie właściwości **narzędzia** menu, kliknij przycisk **opcje**. Rozwiń **środowiska** a następnie kliknij przycisk **czcionki i kolory**.  
  
 Korzystając z tego mechanizmu, należy zaimplementować pakietów VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> interfejsu i jego skojarzone interfejsy.  
  
 W zasadzie mechanizm ten może służyć do modyfikowania wszystkich istniejących **wyświetlania elementów** i **kategorie** zawierające je. Jednak nie można stosować do modyfikowania **EditorCategory tekstu** lub jego **wyświetlania elementów**. Aby uzyskać więcej informacji, zobacz [czcionkę i kolor Przegląd](../extensibility/font-and-color-overview.md).  
  
 Aby zaimplementować niestandardowy **kategorie** lub **wyświetlania elementów**, pakietu VSPackage musi:  
  
- Tworzenie lub identyfikowanie kategorie w rejestrze.  
  
   Implementacja interfejsu środowiska IDE **czcionki i kolory** strona właściwości używa tych informacji do poprawnie zapytań dla usługi obsługi danej kategorii.  
  
- Tworzenie lub identyfikowanie grup (opcjonalnie) w rejestrze.  
  
   Może być przydatne do definiowania grupy, która reprezentuje sumę dwóch lub więcej kategorii. Grupa jest zdefiniowany, IDE automatycznie scala podkategorii i dystrybuuje wyświetlania elementów w obrębie grupy.  
  
- Implementowanie Obsługa środowiska IDE.  
  
- Obsługa zmian czcionek i kolorów.  
  
  Aby uzyskać informacje, zobacz [uzyskiwania dostępu do przechowywanych czcionkę i ustawienia kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Aby utworzyć lub wskazać kategorii  
  
- Konstruowania specjalny rodzaj kategorii wpisu rejestru [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >* \FontAndColors\\`<Category>`]  
  
   *\<Kategoria >* to niezlokalizowana nazwa kategorii.  
  
- Należy wypełnić rejestru za pomocą dwóch wartości:  
  
  |Nazwa|Typ|Dane|Opis|  
  |----------|----------|----------|-----------------|  
  |Kategoria|REG_SZ|Identyfikator GUID|Identyfikator GUID, utworzony w celu identyfikowania tej kategorii.|  
  |Package|REG_SZ|Identyfikator GUID|Identyfikator GUID usługi pakietu VSPackage, która obsługuje kategorii.|  
  
  Usługa określone w rejestrze należy podać implementacja <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> odpowiedniej kategorii.  
  
## <a name="to-create-or-identify-groups"></a>Aby utworzyć lub wskazać grupy  
  
- Konstruowania specjalny rodzaj kategorii wpisu rejestru [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<wersji programu Visual Studio >* \FontAndColors\\  *\<grupy >*]  
  
   *\<grupy >* to niezlokalizowana Nazwa grupy.  
  
- Należy wypełnić rejestru za pomocą dwóch wartości:  
  
  |Nazwa|Typ|Dane|Opis|  
  |----------|----------|----------|-----------------|  
  |Kategoria|REG_SZ|Identyfikator GUID|Identyfikator GUID utworzone, aby zidentyfikować grupę.|  
  |Package|REG_SZ|Identyfikator GUID|Identyfikator GUID usługi, która obsługuje kategorii.|  
  
  Usługa określone w rejestrze należy podać implementacja `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` dla odpowiedniej grupy.  
  
## <a name="to-implement-ide-support"></a>Obsługa środowiska IDE  
  
- Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, która zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu lub `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfejsu środowiska IDE dla każdego **kategorii** lub grupy z podanym identyfikatorem GUID.  
  
- Dla każdego **kategorii** ją obsługuje, pakietu VSPackage implementuje osobne wystąpienie <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> interfejsu.  
  
- Metody implementowane za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> należy podać środowisko IDE z:  
  
  -   Wykazy **wyświetlania elementów** w **kategorii.**  
  
  -   Lokalizowalne nazwy **wyświetlania elementów**.  
  
  -   Wyświetlanie informacji dla każdego elementu członkowskiego **kategorii**.  
  
  > [!NOTE]
  >  Każdy **kategorii** musi zawierać co najmniej jeden **wyświetlanego elementu**.  
  
- IDE używa `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfejs zdefiniowanie sumę kilka kategorii.  
  
   Jego implementacja zapewnia środowisko IDE z:  
  
  -   Lista **kategorie** wchodzące w skład danej grupy.  
  
  -   Dostęp do wystąpienia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> obsługi każdego **kategorii** w obrębie grupy.  
  
  -   Nazwy grup możliwych do zlokalizowania.  
  
- Aktualizowanie środowiska IDE:  
  
   IDE przechowuje informacje o **czcionek i kolorów** ustawienia. Dlatego po każdej modyfikacji IDE **czcionek i kolorów** konfiguracji, zaleca się upewnić, że pamięć podręczna jest nieaktualna.  
  
  Aktualizowanie pamięci podręcznej odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs i mogą być wykonywane globalnie lub tylko na wybranych elementów.  
  
## <a name="to-handle-font-and-color-changes"></a>Aby obsługiwać czcionek i kolorów zmian  
 Aby prawidłowo obsługiwać kolorowanie tekst, który wyświetla pakietu VSPackage, usługa kolorowanie obsługi pakietu VSPackage musi odpowiedzieć na zainicjowanego przez użytkownika zmian za pomocą **czcionki i kolory** stronę właściwości. Pakietu VSPackage to realizowane przez:  
  
-   Obsługa zdarzenia generowane przez środowisko IDE poprzez implementację <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> interfejsu.  
  
     IDE, wywołuje odpowiednią metodę następujące modyfikacje użytkownika **czcionki i kolory** strony. Na przykład wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A> metody, jeśli wybrano opcję nowego czcionki.  
  
     —lub—  
  
-   Sondowanie środowisko IDE przeznaczone do zmiany.  
  
     Można to zrobić za pomocą systemu zaimplementowane <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu. Mimo że przede wszystkim do obsługi trwałości, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> metoda może służyć do uzyskiwania informacji czcionek i kolorów dla **wyświetlania elementów**. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do przechowywanych czcionkę i ustawienia kolorów](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Aby upewnić się, że wyniki uzyskane za pomocą sondowania są poprawne, warto użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> interfejs do ustalenia, czy potrzebne przed wywołaniem metody pobierania czyszczenie pamięci podręcznej i zaktualizuj <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Wprowadzenie czcionkę i kolor informacje dotyczące kolorowania tekstu](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Uzyskiwanie dostępu do przechowywanych czcionkę i kolor ustawienia](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Porady: dostęp do wbudowanych czcionek i schemat kolorów](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Omówienie czcionek i kolorów](../extensibility/font-and-color-overview.md)

