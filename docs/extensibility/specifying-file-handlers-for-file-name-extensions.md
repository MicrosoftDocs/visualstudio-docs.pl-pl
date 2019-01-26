---
title: Określanie programów obsługi plików dla rozszerzeń nazw plików | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1a8814ebf769ba76fe7c1dc6646248a088bc17f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982562"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>Określanie programów obsługi plików dla rozszerzeń nazw plików
Istnieje kilka sposobów, aby określić aplikację, która obsługuje pliku, który ma rozszerzenie określonego pliku. Czasowniki OpenWithList i OpenWithProgids są dwa sposoby określania programów obsługi plików we wpisie rejestru dla rozszerzenia pliku.  
  
## <a name="openwithlist-verb"></a>OpenWithList zlecenia  
 Po kliknięciu prawym przyciskiem myszy plik w Eksploratorze Windows, zobaczysz **Otwórz** polecenia. Jeśli więcej niż jeden produkt jest skojarzony z rozszerzeniem, zobaczysz **Otwórz za pomocą** podmenu.  
  
 Możesz zarejestrować się różne aplikacje, aby otworzyć rozszerzenia, ustawiając klucz OpenWithList dla rozszerzenia pliku w kluczu HKEY_CLASSES_ROOT. Aplikacje tego klucza dla rozszerzenia pliku na liście są wyświetlane w obszarze **zalecanych programów** nagłówek w **Otwórz za pomocą** okno dialogowe. Poniższy przykład pokazuje aplikacje zarejestrowany w celu otwarcia .vcproj rozszerzenie pliku.  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  Klucze, określając aplikacje są na liście w obszarze HKEY_CLASSES_ROOT\Applications.  
  
 Dodanie klucza OpenWithList, zadeklarować, że aplikacja obsługuje rozszerzenie pliku, nawet wtedy, gdy inna aplikacja przejmuje na własność rozszerzenia. Może to być przyszłej wersji aplikacji lub innej aplikacji.  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 Identyfikatory programowe (ProgID) są przyjazne wersje klasy identyfikujące wersję aplikacji lub obiektu COM. Każdy obiekt wspólnie do utworzenia powinny mieć własny identyfikator ProgID. Na przykład VisualStudio.DTE.7.1 uruchamia Visual Studio .NET 2003, podczas uruchamiania VisualStudio.DTE.10.0 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Jako właściciel projektu typu lub typu elementu projektu należy utworzyć identyfikator ProgID specyficzny dla wersji dla rozszerzenia pliku. Te ProgID może być nadmiarowe, w tym, że więcej niż jeden identyfikator ProgID może zostać uruchomiony ta sama aplikacja. Aby uzyskać więcej informacji, zobacz [rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md).  
  
 Aby uniknąć jego duplikowania z rejestracją od innych dostawców, użyj następującej konwencji nazewnictwa dla określonej wersji pliku ProgID:  
  
|Rozszerzenie pliku|Numerów wersji ProgID|  
|--------------------|----------------------|  
|.Extension|ProductName. extension.versionMajor.versionMinor|  
  
 Możesz zarejestrować różne aplikacje, które można otworzyć konkretnego rozszerzenia pliku, dodając numerów wersji ProgID jako wartości przekierowywanie wpisów z HKEY_CLASSES_ROOT\\*\<rozszerzenia >* \OpenWithProgids klucza. Ten klucz rejestru zawiera listę alternatywnych ProgID skojarzone z rozszerzeniem pliku. Aplikacje skojarzone z wymienionych ProgID pojawiają się w **Otwórz za pomocą**_nazwa produktu_ podmenu. Jeśli ta sama aplikacja jest określona w obu `OpenWithList` i `OpenWithProgids` klucze, system operacyjny scala duplikaty.  
  
> [!NOTE]
>  `OpenWithProgids` Klucz jest obsługiwany tylko w Windows XP. Ponieważ inne systemy operacyjne zignorować ten klucz, nie należy używać go jako rejestrację tylko dla programów obsługi plików. Użyj tego klucza, aby zapewnić lepsze środowisko użytkownika w Windows XP.  
  
 Dodaj żądaną ProgID jako wartości typu REG_NONE. Poniższy kod stanowi przykład rejestrowanie ProgID dla rozszerzenia pliku (. *ext*).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 Identyfikator ProgID, określona jako wartość domyślna dla rozszerzenia pliku jest domyślny program obsługi plików. Jeśli zmodyfikujesz ProgID rozszerzenia plików, które są dostarczane z poprzedniej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub mogą być podejmowane przez inne aplikacje, a następnie musisz się zarejestrować, `OpenWithProgids` klucza dla rozszerzenia pliku, a następnie określ nowy identyfikator ProgID na liście wraz z programem stary ProgID, które obsługujesz. Na przykład:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 Jeśli stary identyfikator ProgID ma zleceń skojarzonych z nim, a następnie tych poleceń pojawi się również w obszarze **Otwórz za pomocą** *nazwa produktu* w menu skrótów.  
  
## <a name="see-also"></a>Zobacz też  
 [Temat rozszerzeń nazw plików](../extensibility/about-file-name-extensions.md)   
 [Rejestrowanie zleceń dla rozszerzeń nazw plików](../extensibility/registering-verbs-for-file-name-extensions.md)