---
title: Narzędzie konfiguracji wyświetlania okna | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804840"
---
# <a name="tool-window-display-configuration"></a>Konfiguracja ekranu okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kiedy pakietu VSPackage rejestruje okna narzędzi, domyślne położenie, rozmiar, styl dokowania i inne informacje o widoczności określono opcjonalnych wartości. Aby uzyskać więcej informacji na temat rejestrowanie okna narzędzi, zobacz [narzędzie Windows w rejestrze](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Wyświetl informacje o oknie  
 Konfiguracja podstawowa ekranu okna narzędzi są przechowywane w sześciu wartości opcjonalne:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|Nazwa|REG_SZ|"Krótką nazwę miejsce"|Krótka nazwa opisująca okna narzędzia. Używany tylko w przypadku odwołania w rejestrze.|  
|float|REG_SZ|"X1, Y1, X2, Y2"|Cztery wartości rozdzielonych przecinkami. X1, Y1 jest współrzędnych w lewym górnym rogu okna narzędzia. X2, Y2 jest współrzędną prawym dolnym rogu. Wszystkie wartości są we współrzędnych ekranu.|  
|Styl|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> "Połączone"<br /><br /> "Tabbed"<br /><br /> "AlwaysFloat"|Słowo kluczowe określający początkowej wyświetlenia stanu okna narzędzi.<br /><br /> "MDI" = zadokowane okna MDI.<br /><br /> "Float" = liczb zmiennoprzecinkowych.<br /><br /> "Połączone" = powiązanym z innego okna (określony we wpisie okno).<br /><br /> "Z kartami" = w połączeniu z innego okna narzędzi.<br /><br /> "AlwaysFloat" = nie może być zadokowane.<br /><br /> Aby uzyskać więcej informacji zobacz sekcję uwagi poniżej.|  
|Okno|REG_SZ|*\<GUID>*|Identyfikator GUID okna, do którego okna narzędzi mogą być połączone lub z zakładkami. Identyfikator GUID może należeć do jednej z własnego systemu windows, czy systemu windows w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientacja|REG_SZ|"Left"<br /><br /> "Right"<br /><br /> "Top"<br /><br /> "Dolnej"|Zobacz sekcję uwagi poniżej.|  
|DontForceCreate|REG_DWORD|0 lub 1|Gdy ten wpis jest obecny, a jego wartość nie wynosi zero, okno jest załadowany, ale nie natychmiast wyświetlone.|  
  
### <a name="comments"></a>Komentarze  
 Wpis orientacji definiuje położenie, gdy okno narzędzia dokowane po dwukrotnym kliknięciu paska tytułu. Pozycja jest określana względem okna określony we wpisie okna. Jeśli wpis stylu jest ustawiony na "Połączone", wpis orientacji może być "Left", "Right", "Top" lub "Dolnej". Jeśli wpis styl "Kartach", orientacja wpis może być "Left" lub "Kliknij prawym przyciskiem myszy" i określa, gdzie dodaniu karty. W przypadku wpisu styl "Float", najpierw liczby zmiennoprzecinkowe okna narzędzia. Po dwukrotnym kliknięciu na pasku tytułu Zastosuj wpisy orientacji i okna, a okno używa stylu "Kartach". Okna narzędzi nie może być zadokowane, jeśli wpis stylu jest "AlwaysFloat". Jeśli wpis stylu jest "MDI", okna narzędzi jest połączony obszar MDI i jest ignorowany wpis okna.  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Widoczność okna narzędzi  
 Wartości w podkluczu widoczność Opcjonalnie określ ustawienia widoczność okna narzędzi. Nazwy wartości są używane do przechowywania identyfikatorów GUID poleceń, które wymagają widoczność okna. Jeśli polecenie jest wykonywane, IDE gwarantuje, że okno narzędzia jest utworzony i widoczne.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|(Domyślnie)|REG_SZ|Brak|Pozostaw puste.|  
|*\<GUID>*|REG_DWORD lub REG_SZ|0 lub opisowy ciąg.|Opcjonalna. Nazwa wejścia musi być identyfikator GUID polecenia wymagające widoczności. Wartość zawiera tylko ciąg informacyjny. Zazwyczaj wartość `reg_dword` równa 0.|  
  
### <a name="example"></a>Przykład  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VSPackage Essentials](../misc/vspackage-essentials.md)
