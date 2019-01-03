---
title: Właściwości programu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5743e9532a50089317f0c28917927f514eb4709
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987041"
---
# <a name="msbuild-properties"></a>właściwości programu MSBuild
Właściwości to pary nazwa-wartość, których można używać do konfigurowania kompilacji. Stanową przydatny mechanizm przekazywania wartości do zadań, obliczania warunków i przechowywania wartości, do których będą prowadziły odwołania z różnych miejsc pliku projektu.  
  
## <a name="define-and-reference-properties-in-a-project-file"></a>Definiowanie i odwoływać się do właściwości w pliku projektu  
 Właściwości deklaruje się poprzez utworzenie elementu zawierającego nazwę właściwości jako element podrzędny elementu [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Na przykład następujący kod XML tworzy właściwość o nazwie `BuildDir`, która ma wartość `Build`.  
  
```xml  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 W całym pliku projektu właściwości mają odwołania przy użyciu składni $(\<PropertyName >). Na przykład odwołanie do właściwości z poprzedniego przykładu odbywa się przy użyciu składni $(BuildDir).  
  
 Wartości właściwości można zmieniać poprzez zmianę definicji właściwości. Poniższy kod XML pozwala nadać nową wartość właściwości `BuildDir`:  
  
```xml  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Właściwości są obliczane w kolejności, w jakiej występują w pliku projektu. Nowa wartość właściwości `BuildDir` musi zostać zadeklarowana po przypisaniu starej wartości.  
  
## <a name="reserved-properties"></a>Właściwości zastrzeżone  
 Program MSBuild rezerwuje niektóre nazwy właściwości do przechowywania informacji o pliku projektu oraz pliki binarne programu MSBuild. Odwołania do tych właściwości tworzy się przy użyciu notacji $, podobnie jak w przypadku pozostałych właściwości. Na przykład odwołanie $(MSBuildProjectFile) zwraca pełną nazwę pliku projektu, łącznie z rozszerzeniem.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) i [MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Środowisko — właściwości  
 Odwołania do zmiennych środowiskowych w plikach projektów tworzy się tak samo jako odwołania do właściwości zastrzeżonych. Na przykład aby w pliku projektu użyć zmiennej środowiskowej `PATH`, należy użyć składni $(Path). Jeśli projekt zawiera definicję właściwości o takiej samej nazwie jak właściwość środowiska, właściwość w projekcie zastępuje wartość zmiennej środowiskowej.  
  
 Każdy projekt utworzony w programie MSBuild ma izolowany blok środowiska, tzn. widzi tylko operacje odczytu i zapisu w tym bloku.  Program MSBuild odczytuje zmienne środowiskowe tylko podczas inicjowania kolekcji właściwości, przed obliczeniem i skompilowaniem pliku projektu. Wskutek tej operacji właściwości środowiska stają się statyczne, tzn. każde zainicjowane narzędzie na początku używa tych samych nazw i wartości.  
  
 Aby odczytać bieżące wartości zmiennych środowiskowych z uruchomionego narzędzia, należy użyć [funkcji właściwości](../msbuild/property-functions.md) o nazwie System.Environment.GetEnvironmentVariable. Jednak preferowaną metodą jest użycie parametru zadania <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Właściwości środowiska ustawione w tej tablicy ciągów można przekazywać do zainicjowanego narzędzia bez wpływania na zmienne środowiskowe systemu.  
  
> [!TIP]
>  Nie wszystkie zmienne środowiskowe są wczytywane jako właściwości początkowe. Wszystkie zmienne środowiskowe, którego nazwa jest nieprawidłowa MSBuild właściwości Nazwa, np. "386" jest ignorowany.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Właściwości rejestru  
 Systemu można odczytać wartości rejestru przy użyciu następującej składni, gdzie `Hive` jest gałęzią rejestru (na przykład **HKEY_LOCAL_MACHINE**), `Key` to nazwa klucza `SubKey` jest nazwą podklucza, a `Value`to wartość podklucza.  
  
```xml  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Aby odczytać domyślną wartość podklucza, należy pominąć `Value`.  
  
```xml  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Ta wartość rejestru może służyć do inicjowania właściwości kompilacji. Na przykład w celu utworzenia właściwości kompilacji reprezentującej stronę główną programu Visual Studio w przeglądarce internetowej, należy użyć następującego kodu:  
  
```xml  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Właściwości globalne  
 Program MSBuild umożliwia konfigurowanie właściwości w wierszu polecenia za pomocą **— właściwość** (lub **-p**) przełącznika. Te globalne wartości właściwości zastępują wartości właściwości ustawione w pliku projektu. Dotyczy to również właściwości środowiska, natomiast nie obejmuje właściwości zastrzeżonych, ponieważ nie można ich modyfikować.  
  
 W przykładzie poniżej dla globalnej właściwości `Configuration` jest ustawiana wartość `DEBUG`.  
  
```cmd  
msbuild.exe MyProj.proj -p:Configuration=DEBUG  
```  
  
 Właściwości globalne można także ustawiać i modyfikować dla projektów podrzędnych w kompilacjach wieloprojektowych. Służy do tego atrybut `Properties` zadania programu MSBuild. Właściwości globalne również są przekazywane do projektów podrzędnych, chyba że `RemoveProperties` atrybut zadanie MSBuild służy do określania listy właściwości nie można przesłać dalej. Aby uzyskać więcej informacji, zobacz [zadanie MSBuild](../msbuild/msbuild-task.md).
  
 Jeśli właściwość zostanie określona za pomocą atrybutu `TreatAsLocalProperty` w znaczniku projektu, wartość właściwości globalnej nie zastępuje wartości właściwości ustawionej w pliku projektu. Aby uzyskać więcej informacji, zobacz [Project — element (MSBuild)](../msbuild/project-element-msbuild.md) i [jak: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Funkcje właściwości  
 Począwszy od środowiska .NET Framework w wersji 4 do obliczania skryptów programu MSBuild można używać funkcji właściwości. Funkcje umożliwiają odczytywanie godziny systemowej, porównywanie ciągów tekstowych, porównywanie wyrażeń regularnych i wykonywanie wielu innych czynności w skrypcie kompilacji bez używania zadań programu MSBuild.  
  
 Można używać metod ciągów tekstowych (wystąpień) do wykonywania operacji na dowolnych wartościach właściwości oraz wywoływać metody statyczne wielu klas systemowych. Na przykład za pomocą poniższej składni można ustawić bieżącą datę we właściwość kompilacji:  
  
```xml  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Aby uzyskać więcej informacji i listą funkcji właściwości, zobacz [funkcji właściwości](../msbuild/property-functions.md).  
  
## <a name="create-properties-during-execution"></a>Tworzenie właściwości podczas wykonywania  
 Właściwościom umieszczonym poza elementami `Target` wartości są przypisane w fazie obliczania kompilacji. W następnej fazie (wykonywania) właściwości można tworzyć i modyfikować w następujący sposób:  
  
-   Właściwość może być emitowana przez dowolne zadanie. Aby było wyemitować właściwość, [zadań](../msbuild/task-element-msbuild.md) element musi mieć element podrzędny [dane wyjściowe](../msbuild/output-element-msbuild.md) element, który ma `PropertyName` atrybutu.  
  
-   Właściwość może być emitowana przez [CreateProperty](../msbuild/createproperty-task.md) zadania. Takie użycie jest przestarzałe.  
  
-   Począwszy od platformy .NET Framework w wersji 3.5, elementy `Target` mogą zawierać elementy `PropertyGroup` zawierające deklaracje właściwości.  
  
## <a name="store-xml-in-properties"></a>Store XML we właściwościach  
 Właściwości mogą zawierać dowolny kod XML pomocny w przekazywaniu wartości do zadań albo wyświetlaniu informacji o logowaniu. W przykładzie poniżej pokazano właściwość `ConfigTemplate`, która ma wartość zawierającą kod XML oraz odwołania do innych właściwości. Element [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zastępuje odwołania do właściwości poprzez użycie ich odpowiednich wartości. Wartości właściwości są przypisywane w kolejności, w jakiej występują. Dlatego w tym przykładzie właściwości użyte w odwołaniach `$(MySupportedVersion)`, `$(MyRequiredVersion)` i `$(MySafeMode)` powinny już być zdefiniowane.  
  
```xml  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)"  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)  
 [Instrukcje: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Instrukcje: Odwołanie do nazwy lub lokalizacji pliku projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [Program MSBuild zarezerwowane i dobrze znane właściwości](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property — element (MSBuild)](../msbuild/property-element-msbuild.md)
