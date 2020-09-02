---
title: Wspólne elementy projektów MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e36d5e50b15a5ede425715ec756f05ab8d014de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160405"
---
# <a name="common-msbuild-project-items"></a>Wspólne elementy projektów MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] element jest nazwanym odwołaniem do co najmniej jednego pliku. Elementy zawierają metadane, takie jak nazwy plików, ścieżki i numery wersji. Wszystkie typy projektów w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mają kilka elementów wspólnych. Te elementy są zdefiniowane w pliku Microsoft. Build. CommonTypes. xsd.  
  
## <a name="common-items"></a>Elementy wspólne  
 Poniżej znajduje się lista wszystkich wspólnych elementów projektu.  
  
### <a name="reference"></a>Dokumentacja  
 Reprezentuje odwołanie zestawu (zarządzanego) w projekcie.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|HintPath|Opcjonalny ciąg. Ścieżka względna lub bezwzględna zestawu.|  
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana zestawu, na przykład "System. Windows. Forms".|  
|FusionName|Opcjonalny ciąg. Określa prostą lub silną nazwę syntezy dla elementu.<br /><br /> Gdy ten atrybut jest obecny, może zaoszczędzić czas, ponieważ plik zestawu nie musi być otwarty w celu uzyskania nazwy Fusion.|  
|Ustawienie SpecificVersion|Opcjonalna wartość logiczna. Określa, czy należy odwoływać się tylko do wersji w nazwie Fusion.|  
|Aliasy|Opcjonalny ciąg. Wszelkie aliasy odwołania.|  
|Prywatne|Opcjonalna wartość logiczna. Określa, czy odwołanie ma być kopiowane do folderu wyjściowego. Ten atrybut jest zgodny z właściwością **copy lokalnego** odwołania, która znajduje się w środowisku IDE programu Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Reprezentuje odwołanie do składnika COM (niezarządzane) w projekcie.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana składnika.|  
|Guid (identyfikator GUID)|Opcjonalny ciąg. Identyfikator GUID składnika w formularzu {12345678-1234-1234-1234-1234567891234} .|  
|VersionMajor|Opcjonalny ciąg. Główna część numeru wersji składnika. Na przykład "5", jeśli pełny numer wersji to "5,46".|  
|VersionMinor|Opcjonalny ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46", jeśli pełny numer wersji to "5,46".|  
|Identyfikator LCID|Opcjonalny ciąg. LocaleID dla składnika.|  
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, które jest używane w składniku, na przykład "tlbimp".|  
|Izolowana|Opcjonalna wartość logiczna. Określa, czy składnik jest składnikiem bezpłatnym reg.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Reprezentuje listę bibliotek typów, które są źródłem do elementu docelowego ResolvedComreference.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, które jest używane w składniku, na przykład "tlbimp".|  
  
### <a name="nativereference"></a>NativeReference  
 Reprezentuje natywny plik manifestu lub odwołanie do takiego pliku.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Wymagany ciąg. Podstawowa nazwa pliku manifestu.|  
|HintPath|Wymagany ciąg. Ścieżka względna pliku manifestu.|  
  
### <a name="projectreference"></a>Elementu ProjectReference  
 Reprezentuje odwołanie do innego projektu.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana odwołania.|  
|Projekt|Opcjonalny ciąg. Identyfikator GUID odwołania w formularzu {12345678-1234-1234-1234-1234567891234} .|  
|Pakiet|Opcjonalny ciąg. Ścieżka do pliku projektu, do którego istnieje odwołanie.|  
  
### <a name="compile"></a>Opracowania  
 Reprezentuje pliki źródłowe kompilatora.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie.|  
|AutoGen|Opcjonalna wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowane środowisko programistyczne (IDE).|  
|Link|Opcjonalny ciąg. Ścieżka zapisu, która ma być wyświetlana, gdy plik jest fizycznie zlokalizowany poza wpływem pliku projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany **Solution Explorer** w Eksplorator rozwiązań [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Reprezentuje zasoby do osadzenia w wygenerowanym zestawie.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować prawidłowo|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod.|  
|Link|Opcjonalny ciąg. Ścieżka notacji jest wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany **Solution Explorer** w Eksplorator rozwiązań [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest|  
|Logicznaname|Wymagany ciąg. Nazwa logiczna zasobu osadzonego.|  
  
### <a name="content"></a>Zawartość  
 Reprezentuje pliki, które nie są kompilowane do projektu, ale mogą być osadzone lub opublikowane razem z nim.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie.|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod.|  
|Link|Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany **Solution Explorer** w Eksplorator rozwiązań [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|PublishState|Wymagany ciąg. Stan publikowania zawartości:<br /><br /> -Domyślne<br />-Uwzględnione<br />-Wykluczone<br />-Plik<br />-Wymaganie wstępne|  
|IsAssembly|Opcjonalna wartość logiczna. Określa, czy plik jest zestawem.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany **Solution Explorer** w Eksplorator rozwiązań [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest|  
  
### <a name="none"></a>Brak  
 Reprezentuje pliki, które nie powinny mieć roli w procesie kompilacji.  
  
|Nazwa elementu|Opis|  
|---------------|-----------------|  
|DependentUpon|Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie.|  
|Generator|Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie.|  
|LastGenOutput|Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie.|  
|CustomToolNamespace|Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod.|  
|Link|Opcjonalny ciąg. Ścieżka notacji, która ma być wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu.|  
|Widoczne|Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany **Solution Explorer** w Eksplorator rozwiązań [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Reprezentuje podstawowy manifest aplikacji dla kompilacji i zawiera [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Informacje o zabezpieczeniach wdrożenia.  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Reprezentuje projekt FxCop do zaimportowania.  
  
### <a name="import"></a>Importuj  
 Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilator.  
  
## <a name="see-also"></a>Zobacz też  
 [Wspólne właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
