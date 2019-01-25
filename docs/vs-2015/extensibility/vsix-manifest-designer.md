---
title: VSIX Manifest Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 308259e7addcf41ae6e15191934a8c37ac3f57b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54752329"
---
# <a name="vsix-manifest-designer"></a>Projektant manifestu VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modyfikuje VSIX plik manifestu pakietu, który określa zachowanie podczas instalacji rozszerzenia programu Visual Studio.  
  
 **Projektant manifestu VSIX** mapuje schemat źródłowy VSIX. Każdy element w schemacie można ustawić za pomocą odpowiedniego formantu w projektancie. Aby uzyskać więcej informacji na temat schematu, zobacz [VSIX rozszerzenia schematu 2.0 Reference](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Aby otworzyć **Projektant manifestu VSIX**, zlokalizuj plik source.extension.vsixmanifest w **Eksploratora rozwiązań**i Otwórz plik. Jeśli plik nie zawiera prawidłowy kod XML, Projektant manifestu nie zostanie otwarty.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest przekazywane są do extension.vsixmanifest podczas tworzenia pakietu.  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Projektant manifestu VSIX** zawiera cztery sekcje, które odnoszą się do tych elementów najwyższego poziomu schematu:  
  
- Metadane  
  
- Elementy docelowe instalacji  
  
- Elementy zawartości  
  
- Zależności  
  
  W obszarze nagłówka zawiera następujące elementy sterujące.  
  
  **Nazwa produktu**  
  W tym artykule opisano Nazwa rozszerzenia.  
  
  **Identyfikator produktu**  
  Określa unikatową identyfikację tego pakietu.  
  
  **Autor**  
  Określa nazwę autora rozszerzenia.  
  
  **Wersja**  
  Określa numer wersji rozszerzenia.  
  
  **Metadanych** karta zawiera następujące elementy sterujące.  
  
  **Opis**  
  Zawiera opis tekstowy rozszerzenia mają być wyświetlane w **Menedżera rozszerzeń**.  
  
  **Język**  
  Określa domyślny język dla pakietu, który odnosi się do danych tekstowych w manifeście. `Language` Atrybut następuje typową Konwencją kod ustawień regionalnych języka wspólnego (CLR) dla zestawów zasobów, na przykład en-us, en, fr-fr. Domyślnie wartość jest neutralne; oznacza to, że pakiet będzie działać w dowolnej wersji językowej programu Visual Studio.  
  
  **Licencja**  
  Określa plik tekstowy, który zawiera licencji użytkownika, jeśli jest obecna.  
  
  **Ikona**  
  Określa plik graphics (PNG, bmp, JPEG, .ico), który zawiera ikonę do wyświetlenia w **Menedżera rozszerzeń**, jeśli występuje ikona. Obraz ikony musi być 32 x 32 piksele lub jego rozmiar zostanie zmieniony na te wymiary. Jeśli określono żadnej ikony, **Menedżera rozszerzeń** używa ikona domyślna.  
  
  **Obraz podglądu**  
  Określa plik graphics (PNG, bmp, JPEG, .ico), który zawiera obraz podglądu, które mają być wyświetlane w **Menedżera rozszerzeń**, jeśli obraz podglądu jest obecny. Obraz podglądu musi być 200 x 200 pikseli. Jeśli brak obrazu (wersja zapoznawcza) jest określony, **Menedżera rozszerzeń** korzysta z domyślnego obrazu.  
  
  **Tagi**  
  Dodaje znaczniki tekst służący do wskazówki dotyczące wyszukiwania.  
  
  **Uwagi do wersji**  
  Określa plik (.txt, RTF), który zawiera informacje o wersji. Pobiera również adres URL witryny sieci Web, która wyświetla informacje o wersji.  
  
  **Wprowadzenie — przewodnik**  
  Określa plik (.txt, RTF), który zawiera informacje o sposobie używania rozszerzenia lub zawartości w pakiecie VSIX. Ten przewodnik jest wyświetlany, gdy instalacja rozszerzenia została ukończona. Pobiera również adres URL witryny sieci Web, która wyświetla przewodnika.  
  
  **Więcej informacji o adres URL.**  
  Określa adres URL witryny sieci Web, która zawiera dodatkowe informacje o produkcie.  
  
  **Instaluj obiekty docelowe** karta zawiera następujące elementy sterujące.  
  
  **Typ instalacji**  
  Wyświetla listę **rozszerzenie programu Visual Studio** i **zestaw SDK rozszerzeń** docelowy jako typy instalacji. Opcje różnią się w zależności od wybranego typu.  
  
  **Visual Studio Extension**  
  Wyświetla listę **InstallationTarget** elementy, które opisują, jak można zainstalować pakietu i do produktów Visual Studio, które można zainstalować tego rozszerzenia. Każdy produkt został zidentyfikowany osobno według nazwy i wersji lub zakresu.  Produkty mogą dodany do listy, modyfikacji i usunięte. Nazwa i wersja produktu odpowiadają **identyfikator** i **wersji** atrybuty skojarzonego **InstallationTarget** elementu.  
  
  **Zakres wersji** jest [12.0, 14,0] i używa następujący zapis:  
  
- [— minimalna wersja (włącznie)  
  
- ] — maksymalna wersja (włącznie)  
  
- (— minimalna wersja wyłączne  
  
- ) — maksymalna wersja wyłączne  
  
- Jednej wersji # - tylko określona wersja  
  
  **Zestaw SDK rozszerzenia**  
  Określa globalny instalacja, która nie jest ograniczone do określonego produktu i wersji. **Identyfikator platformy docelowej** to platforma, takie jak "Windows", gdy elementem docelowym. **Wersja platformy docelowej** jest wersji, takich jak 8.0 z docelowej platformy. **Nazwa zestawu SDK** i **wersja zestawu SDK** są nazwa i numer wersji zestawu SDK, odpowiednio.  
  
  **Plik VSIX są zainstalowane dla wszystkich użytkowników (wymaga podniesienia uprawnień związane z instalacją)** pola wyboru  
  Jeśli to pole wyboru jest zaznaczone, to rozszerzenie jest zainstalowane dla wszystkich użytkowników. w przeciwnym razie jest zainstalowany tylko dla bieżącego użytkownika.  
  
  **Plik VSIX jest instalowany przez Instalatora Windows** pola wyboru  
  Jeśli to pole wyboru jest zaznaczone, to rozszerzenie jest zainstalowane przez Instalatora Windows (plik msi); w przeciwnym razie jest ona instalowana jako typowych pakietów VSIX (plik .vsix).  
  
  **Zasoby** karta zawiera następujące elementy sterujące.  
  
  **Lista zasobów**  
  Wyświetla elementy zawartości, które opisują rozszerzenia lub zawartości elementów że pakietu powierzchnie. Każdego rozszerzenia lub zawartości elementu jest wyświetlany osobno według źródła, typu i ścieżki. Rozszerzenia i zawartości elementy można dodany do listy, modyfikować i usunięte. Typ i ścieżki rozszerzenia lub zawartości elementu odpowiada `Type` i `Path` atrybuty skojarzonego `Asset` elementu. Znane są następujące typy:  
  
- Microsoft.VisualStudio.Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft.VisualStudio.ToolboxControl  
  
- Microsoft.VisualStudio.Samples  
  
- Microsoft.VisualStudio.ProjectTemplate  
  
- Microsoft.VisualStudio.ItemTemplate  
  
- Microsoft.VisualStudio.Assembly  
  
- Microsoft.ExtensionSDK  
  
  Można dodawać lub edytować element zawartości, należy określić typ zawartości, czy zasób jest projekt w bieżącym rozwiązaniu lub pliku w systemie plików, a nazwa projektu. Można również określić nazwę folderu, w którym ma zostać osadzony.  
  
  Można również utworzyć własne typy i nadaj im nazwy unikatowe.  
  
  **Zależności** karta zawiera następujące elementy sterujące.  
  
  **Nazwa źródła i zakresu wersji.**  
  Wyświetla listę elementów zależności tego pakietu, które są inne pakiety, od których zależy ten pakiet. Jeśli zostanie określona zależność pakietu, należy zainstalować przed zainstalowaniem tego pakietu; w przeciwnym razie tego pakietu należy go zainstalować.  
  
  Zależności pakietów są określone przez identyfikator, nazwę, zakres wersji, źródła i jak zależność ma zostać rozwiązany. Każdy pakiet zależności jest wyświetlany osobno według nazwy, wersji i źródła. Pakiety zależności mogą być dodawane do listy, zmodyfikowane lub usunięte.  
  
  Identyfikator musi być zgodna `ID` atrybut metadane pakietów zależności. Źródło może być projektu w bieżącym rozwiązaniu, obecnie zainstalowanego rozszerzenia lub pliku. **Jest jak rozpoznać zależności** ustawienie może być ścieżki względnej w zagnieżdżonych pakietu lub adres URL lokalizacji pobierania dla zależności. Identyfikator wersji i rozwiązania pakietu zależności odpowiadają `Id`, `Version`, i `Location` atrybuty skojarzonego `Dependency` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)
