---
title: Konfiguracja wyświetlania okna narzędzi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186394"
---
# <a name="tool-window-display-configuration"></a>Konfiguracja wyświetlania okna narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy pakietu VSPackage rejestruje okno narzędzi, domyślne położenie, rozmiar, styl dokowania i inne informacje o widoczności są określone w opcjonalnych wartościach. Aby uzyskać więcej informacji o rejestracji okna narzędzi, zobacz [okna narzędzi w rejestrze](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informacje o wyświetlaniu okna  
 Podstawowa konfiguracja wyświetlania okna narzędzi jest przechowywana w maksymalnie sześciu wartościach opcjonalnych:  
  
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
|Nazwa|REG_SZ|"Miejsce na krótką nazwę"|Krótka nazwa opisująca okno narzędzia. Używane tylko w przypadku odwołania w rejestrze.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Cztery wartości rozdzielone przecinkami. X1, Y1 to współrzędna lewego górnego rogu okna narzędzi. X2, Y2 to współrzędna prawego dolnego rogu. Wszystkie wartości są we współrzędnych ekranu.|  
|Styl|REG_SZ|MDI<br /><br /> Float<br /><br /> Połączone<br /><br /> Z kartami<br /><br /> "AlwaysFloat"|Słowo kluczowe określające początkowy stan wyświetlania okna narzędzi.<br /><br /> "MDI" = zadokowany z oknem MDI.<br /><br /> "Float" = zmiennoprzecinkowe.<br /><br /> "Połączone" = połączone z innym oknem (określone w pozycji okna).<br /><br /> "Z kartami" = połączony z innym oknem narzędzia.<br /><br /> "AlwaysFloat" = nie można zadokować.<br /><br /> Aby uzyskać więcej informacji, zobacz sekcję komentarze poniżej.|  
|Okno|REG_SZ|*\<GUID>*|Identyfikator GUID okna, do którego można połączyć okno narzędzi lub karta. Identyfikator GUID może należeć do jednego z własnych okien lub jednego z okien w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.|  
|Orientacja|REG_SZ|Lewym<br /><br /> Kliknij<br /><br /> Najwyższą<br /><br /> Stop|Zapoznaj się z sekcją komentarze poniżej.|  
|DontForceCreate|REG_DWORD|0 lub 1|Gdy ten wpis jest obecny i jego wartość nie jest równa zero, okno zostanie załadowane, ale nie jest natychmiast wyświetlane.|  
  
### <a name="comments"></a>Komentarze  
 Wpis orientacji definiuje położenie, w którym okno narzędzia zostanie zadokowane po dwukrotnym kliknięciu paska tytułu. Pozycja jest względem okna określonego w pozycji okna. Jeśli wpis stylu jest ustawiony na "połączone", wpis orientacji może mieć wartość "Left", "Right", "Top" lub "Bottom". Jeśli wpis stylu jest "z kartami", wpis orientacji może mieć wartość "Left" lub "Right" i określać, gdzie karta jest dodawana. Jeśli pozycja stylu jest "float", okno narzędzia zostanie przepływane jako pierwsze. Po dwukrotnym kliknięciu paska tytułu stosowane są pozycje orientacji i okna, a w oknie zostanie użyty styl "Karta". Jeśli pozycja stylu ma wartość "AlwaysFloat", nie można zadokować okna narzędzi. Jeśli wpis stylu to "MDI", okno narzędzia jest połączone z obszarem MDI, a wpis okna jest ignorowany.  
  
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
 Wartości w nieopcjonalnym podkluczu widoczności określają ustawienia widoczności okna narzędzi. Nazwy wartości są używane do przechowywania identyfikatorów GUID poleceń, które wymagają widoczności okna. Jeśli polecenie zostanie wykonane, IDE gwarantuje, że okno narzędzia jest tworzone i wyświetlane.  
  
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
|*\<GUID>*|REG_DWORD lub REG_SZ|0 lub ciąg opisowy.|Opcjonalny. Nazwa wpisu musi być identyfikatorem GUID polecenia wymagającego widoczności. Wartość tylko zawiera ciąg informacyjny. Zazwyczaj wartość jest równa `reg_dword` 0.|  
  
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
 [Pakietu VSPackage Essentials](../misc/vspackage-essentials.md)
