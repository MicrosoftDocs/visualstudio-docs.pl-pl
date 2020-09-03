---
title: Funkcje właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4108e478e9e77a5ed5699b39dfae44884a6befd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826175"
---
# <a name="property-functions"></a>Funkcje właściwości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W .NET Framework wersjach 4 i 4,5 funkcja właściwości może służyć do oceniania skryptów programu MSBuild. Funkcji właściwości można używać wszędzie tam, gdzie są wyświetlane właściwości. W przeciwieństwie do zadań, funkcji właściwości można używać poza obiektami docelowymi i są oceniane przed dowolnymi uruchomieniami docelowym.  
  
 Bez używania zadań programu MSBuild można odczytać czas systemowy, porównać ciągi, dopasować wyrażenia regularne i wykonać inne akcje w skrypcie kompilacji. Program MSBuild podejmie próbę przekonwertowania ciągu na liczbę i liczbę na ciąg, a następnie wprowadzi inne konwersje zgodnie z wymaganiami.  
  
 **W tym temacie:**  
  
- [Składnia funkcji właściwości](#BKMK_Syntax)  
  
  - [Funkcje właściwości ciągu](#BKMK_String)  

  - [Statyczne funkcje właściwości](#BKMK_Static)  

  - [Wywoływanie metod wystąpienia właściwości statycznych](#BKMK_InstanceMethods)  

  - [Funkcje właściwości programu MSBuild](#BKMK_PropertyFunctions)  
  
- [Funkcje właściwości zagnieżdżonych](#BKMK_Nested)  
  
- [DoesTaskHostExist MSBuild](#BKMK_DoesTaskHostExist)  
  
- [GetDirectoryNameOfFileAbove MSBuild](#BKMK_GetDirectoryNameOfFileAbove)  
  
- [GetRegistryValue MSBuild](#BKMK_GetRegistryValue)  
  
- [GetRegistryValueFromView MSBuild](#BKMK_GetRegistryValueFromView)  
  
- [MakeRelative MSBuild](#BKMK_MakeRelative)  
  
- [ValueOrDefault MSBuild](#BKMK_ValueOrDefault)  
  
## <a name="property-function-syntax"></a><a name="BKMK_Syntax"></a> Składnia funkcji właściwości  
 Są to trzy rodzaje funkcji właściwości; Każda funkcja ma inną składnię:  
  
- Funkcje właściwości String (Instance)  
  
- Statyczne funkcje właściwości  
  
- Funkcje właściwości programu MSBuild  
  
### <a name="string-property-functions"></a><a name="BKMK_String"></a> Funkcje właściwości ciągu  
 Wszystkie wartości właściwości kompilacji są tylko wartościami ciągu. Można użyć metod String (Instance) do działania na dowolnej wartości właściwości. Na przykład można wyodrębnić nazwę dysku (pierwsze trzy znaki) z właściwości build, która reprezentuje pełną ścieżkę przy użyciu tego kodu:  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
### <a name="static-property-functions"></a><a name="BKMK_Static"></a> Statyczne funkcje właściwości  
 W skrypcie kompilacji można uzyskać dostęp do właściwości statycznych i metod wielu klas systemowych. Aby uzyskać wartość właściwości statycznej, użyj następującej składni, gdzie *Class* to nazwa klasy systemowej i *Właściwość* jest nazwą właściwości.  
  
 `$([Class]::Property)`  
  
 Na przykład można użyć poniższego kodu, aby ustawić właściwość kompilacji na bieżącą datę i godzinę.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Aby wywołać metodę statyczną, należy użyć następującej składni, gdzie *Class* jest nazwą klasy systemowej, *Metoda* jest nazwą metody, a *(Parameters)* jest listą parametrów dla metody:  
  
 `$([Class]::Method(Parameters))`  
  
 Na przykład, aby ustawić właściwość kompilacja na nowy identyfikator GUID, można użyć tego skryptu:  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 W funkcjach właściwości statycznych można użyć dowolnej statycznej metody lub właściwości tych klas systemu:  
  
- System. Byte  
  
- System. Char  
  
- System. Convert  
  
- System. DateTime  
  
- System. Decimal  
  
- System. Double  
  
- System. Enum  
  
- System. GUID  
  
- System. Int16  
  
- System. Int32  
  
- System. Int64  
  
- System. IO. Path  
  
- System. Math  
  
- System. UInt16  
  
- System. UInt32  
  
- System. UInt64  
  
- System. nadana  
  
- System. Single  
  
- System. String  
  
- System. StringComparer  
  
- System. TimeSpan  
  
- System. Text. RegularExpressions. wyrażenie regularne  
  
- Microsoft. Build. Utilities. ToolLocationHelper  
  
  Ponadto można użyć następujących metod statycznych i właściwości:  
  
- System. Environment:: CommandLine  
  
- System. Environment:: ExpandEnvironmentVariables  
  
- System. Environment:: GetEnvironmentVariable  
  
- System. Environment:: GetEnvironmentVariables  
  
- System. Environment:: GetFolderPath  
  
- System. Environment:: GetLogicalDrives  
  
- System. IO. Directory:: getreżysers  
  
- System. IO. Directory:: GetFiles  
  
- System. IO. Directory:: GetLastAccessTime  
  
- System. IO. Directory:: GetLastWriteTime  
  
- System. IO. Directory:: GetParent  
  
- System. IO. File:: istnieje  
  
- System. IO. File:: GetCreationTime  
  
- System. IO. File:: GetAttributes  
  
- System. IO. File:: GetLastAccessTime  
  
- System. IO. File:: GetLastWriteTime  
  
- System. IO. File:: ReadAllText obiektu  
  
### <a name="calling-instance-methods-on-static-properties"></a><a name="BKMK_InstanceMethods"></a> Wywoływanie metod wystąpienia właściwości statycznych  
 Jeśli uzyskujesz dostęp do właściwości statycznej, która zwraca wystąpienie obiektu, można wywołać metody instancji tego obiektu. Aby wywołać metodę wystąpienia, użyj następującej składni, gdzie *Class* jest nazwą klasy systemowej, *Właściwość* jest nazwą właściwości, *Metoda* jest nazwą metody, a *(parametry)* jest listą parametrów dla metody:  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Nazwa klasy musi być w pełni kwalifikowana z przestrzenią nazw.  
  
 Na przykład można użyć poniższego kodu, aby ustawić właściwość kompilacja na bieżącą datę dzisiejszą.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
### <a name="msbuild-property-functions"></a><a name="BKMK_PropertyFunctions"></a> Funkcje właściwości programu MSBuild  
 Można uzyskać dostęp do kilku metod statycznych w kompilacji, aby zapewnić obsługę znaków arytmetycznych, koniunkcji logicznej i ucieczki. Dostęp do tych metod uzyskuje się za pomocą następującej składni, gdzie *Metoda* jest nazwą metody, a *Parametry* jest listą parametrów dla metody.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Aby na przykład dodać dwa właściwości, które mają wartości liczbowe, użyj poniższego kodu.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
 Poniżej znajduje się lista funkcji właściwości programu MSBuild:  
  
|Sygnatura funkcji|Opis|  
|------------------------|-----------------|  
|podwójne dodanie (podwójne a, podwójne b)|Dodaj dwa podwojone.|  
|długie dodanie (Long a, Long b)|Dodaj dwa długie.|  
|podwójne odejmowanie (podwójne a, podwójne b)|Odejmij dwa podwójnej precyzji.|  
|Długa odejmowanie (Long a, Long b)|Odejmij dwie długości.|  
|Podwójna pomnóż (podwójna a, Double b)|Pomnóż dwa podwojone.|  
|Long pomnóż (Long a, Long b)|Pomnóż dwie długości.|  
|podwójne dzielenie (podwójne a, podwójne b)|Podziel dwa podwojone.|  
|Długa dzielenie (Long a, Long b)|Podziel dwie długości.|  
|podwójne modulo (Double a, Double b)|Dwukrotne dzielenie modulo.|  
|długie modulo (Long a, Long b)|Modulo dwa długie.|  
|ciąg ucieczki (ciąg niezmieniony)|Wypróbowanie ciągu zgodnie z regułami ucieczki MSBuild.|  
|ciąg Unescape (ciąg ucieczki)|Usuń znak ucieczki, zgodnie z regułami ucieczki MSBuild.|  
|int bitowego (int First, int Second)|Wykonaj bitowe `OR` od pierwszego i drugiego (pierwszy &#124; sekundę).|  
|int BitwiseAnd (int First, int Second)|Wykonaj bitowe `AND` od pierwszego i drugiego (pierwszy & sekundę).|  
|int BitwiseXor (int First, int Second)|Wykonaj bitowe `XOR` od pierwszego i drugiego (pierwszy ^ s).|  
|int BitwiseNot (najpierw int)|Wykonaj wartość bitową `NOT` (po pierwszej).|  
  
## <a name="nested-property-functions"></a><a name="BKMK_Nested"></a> Funkcje właściwości zagnieżdżonych  
 Można połączyć funkcje właściwości, aby tworzyć bardziej złożone funkcje, jak pokazano w poniższym przykładzie.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Ten przykład zwraca wartość <xref:System.IO.FileAttributes> `Archive` bitu (32 lub 0) pliku dostarczonego przez ścieżkę `tempFile` . Zauważ, że wartości wyliczane danych nie mogą występować według nazwy w ramach funkcji właściwości. Zamiast tego należy użyć wartości liczbowej (32).  
  
 Metadane mogą być również wyświetlane w zagnieżdżonych funkcjach właściwości. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).  
  
## <a name="msbuild-doestaskhostexist"></a><a name="BKMK_DoesTaskHostExist"></a> DoesTaskHostExist MSBuild  
 `DoesTaskHostExist`Funkcja właściwości w programie MSBuild zwraca, czy host zadania jest aktualnie zainstalowany dla określonych wartości środowiska uruchomieniowego i architektury.  
  
 Ta funkcja właściwości ma następującą składnię:  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
## <a name="msbuild-getdirectorynameoffileabove"></a><a name="BKMK_GetDirectoryNameOfFileAbove"></a> GetDirectoryNameOfFileAbove MSBuild  
 `GetDirectoryNameOfFileAbove`Funkcja właściwości programu MSBuild szuka pliku w katalogach znajdujących się powyżej bieżącego katalogu w ścieżce.  
  
 Ta funkcja właściwości ma następującą składnię:  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 Poniższy kod jest przykładem tej składni.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
## <a name="msbuild-getregistryvalue"></a><a name="BKMK_GetRegistryValue"></a> GetRegistryValue MSBuild  
 `GetRegistryValue`Funkcja właściwości programu MSBuild zwraca wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty, nazwę klucza i nazwę wartości oraz zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości, zwracana jest wartość domyślna.  
  
 W poniższych przykładach pokazano, jak ta funkcja jest używana:  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
## <a name="msbuild-getregistryvaluefromview"></a><a name="BKMK_GetRegistryValueFromView"></a> GetRegistryValueFromView MSBuild  
 `GetRegistryValueFromView`Funkcja właściwości programu MSBuild pobiera dane rejestru systemowego, uwzględniając klucz rejestru, wartość i co najmniej jeden uporządkowany widok rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności, aż zostaną znalezione.  
  
 Składnia tej funkcji właściwości to:  
  
 [MSBuild \] :: GetRegistryValueFromView (ciąg KeyName, wartość ciągu, objectvalue, params obiektu [] widoki)  
  
 System operacyjny Windows 64-bitowy HKEY_LOCAL_MACHINE obsługuje klucz rejestru \SOFTWARE\Wow6432Node, który przedstawia HKEY_LOCAL_MACHINE widok rejestru \SOFTWARE dla aplikacji 32-bitowych.  
  
 Domyślnie aplikacja 32-bitowa działająca w emulatorze WOW64 uzyskuje dostęp do widoku rejestru 32-bitowego, a aplikacja 64-bit uzyskuje dostęp do widoku rejestru 64-bitowego.  
  
 Dostępne są następujące widoki rejestru:  
  
|Widok rejestru|Definicja|  
|-------------------|----------------|  
|RegistryView.Registry32|Widok rejestru aplikacji 32-bitowych.|  
|RegistryView.Registry64|Widok rejestru aplikacji 64-bitowych.|  
|RegistryView. default|Widok rejestru, który jest zgodny z procesem, w którym działa aplikacja.|  
  
 Poniżej przedstawiono przykład.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 Pobiera dane SLRuntimeInstallPath klucza ReferenceAssemblies, najpierw szukając w widoku rejestru 64-bitowego, a następnie w widoku rejestru 32-bitowego.  
  
## <a name="msbuild-makerelative"></a><a name="BKMK_MakeRelative"></a> MakeRelative MSBuild  
 `MakeRelative`Funkcja właściwości programu MSBuild zwraca ścieżkę względną drugiej ścieżki względem pierwszej ścieżki. Każda ścieżka może być plikiem lub folderem.  
  
 Ta funkcja właściwości ma następującą składnię:  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
```  
  
 Poniższy kod jest przykładem tej składni.  
  
```xml  
<PropertyGroup>  
    <Path1>c:\users\</Path1>  
    <Path2>c:\users\username\</Path2>  
</PropertyGroup>  
  
<Target Name = "Go">  
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />  
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />  
</Target>  
  
<!--  
Output:  
   username\  
   ..\  
-->  
```  
  
## <a name="msbuild-valueordefault"></a><a name="BKMK_ValueOrDefault"></a> ValueOrDefault MSBuild  
 `ValueOrDefault`Funkcja właściwości programu MSBuild zwraca pierwszy argument, chyba że jest to wartość zerowa lub pusta. Jeśli pierwszy argument ma wartość null lub jest pusty, funkcja zwraca drugi argument.  
  
 Poniższy przykład pokazuje, jak ta funkcja jest używana.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
    </PropertyGroup>  
  
    <Target Name="MyTarget">  
        <Message Text="Value1 = $(Value1)" />  
        <Message Text="Value2 = $(Value2)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Value1 = a  
  Value2 = b  
-->  
```

## <a name="see-also"></a>Zobacz też
[Właściwości programu MSBuild](msbuild-properties1.md)   
[Omówienie programu MSBuild](msbuild.md)
