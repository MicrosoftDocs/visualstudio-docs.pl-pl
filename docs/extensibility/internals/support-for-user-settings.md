---
title: Obsługa ustawień użytkownika | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704788"
---
# <a name="support-for-user-settings"></a>Pomoc techniczna dotycząca ustawień użytkownika
Pakietu VSPackage może definiować jedną lub więcej kategorii ustawień, które są grupami zmiennych stanu, które są zachowywane, gdy użytkownik wybierze polecenie **Importuj/Eksportuj ustawienia** w menu **Narzędzia** . Aby włączyć tę trwałość, Użyj ustawień API w [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Wpis rejestru, który jest określany jako punkt ustawień niestandardowych, a identyfikator GUID definiuje kategorię ustawień pakietu VSPackage. Pakietu VSPackage może obsługiwać wiele kategorii ustawień, z których każda została zdefiniowana przez punkt ustawień niestandardowych.

- Implementacje ustawień, które są oparte na zestawach międzyoperacyjnych (przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfejsu), powinny utworzyć punkt ustawień niestandardowych przez edycję rejestru lub użycie skryptu rejestratora (plik. RGS). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](/cpp/atl/creating-registrar-scripts).

- Kod, który używa struktury zarządzanego pakietu (MPF), powinien utworzyć punkty ustawień niestandardowych przez dołączenie <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> do pakietu VSPackage dla każdego punktu ustawień niestandardowych.

     Jeśli pojedynczy pakietu VSPackage obsługuje kilka punktów ustawień niestandardowych, każdy punkt ustawień niestandardowych jest implementowany przez oddzielną klasę, a każdy z nich jest rejestrowany przez unikatowe wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasy. W związku z tym ustawienia implementujące klasy mogą obsługiwać więcej niż jedną kategorię ustawień.

## <a name="custom-settings-point-registry-entry-details"></a>Szczegóły wpisu rejestru punktu ustawień niestandardowych
 Punkty ustawień niestandardowych są tworzone we wpisie rejestru w następującej lokalizacji: HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings \\ `<CSPName>` , gdzie `<CSPName>` to nazwa punktu ustawień niestandardowych, który obsługuje pakietu VSPackage i *\<Version>* jest wersją programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , na przykład 8,0.

> [!NOTE]
> Ścieżka katalogu głównego HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* może być zastąpiona alternatywnym elementem głównym, gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest inicjowane zintegrowane środowisko programistyczne (IDE). Aby uzyskać więcej informacji, zobacz [przełączniki wiersza polecenia](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Poniżej przedstawiono strukturę wpisu rejestru:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= s "#12345"

 Package = "{XXXXXX XXXX XXXX XXXXXXXXX}"

 Kategoria = "{YYYYYY rrrr rrrr rrrr YYYYYYYYY}"

 ResourcePackage = "{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}"

 AlternateParent = CategoryName

| Nazwa | Typ | Dane | Opis |
|-----------------|--------| - | - |
| (Domyślnie) | REG_SZ | Nazwa punktu ustawień niestandardowych | Nazwa klucza, `<CSPName`>, to nielokalna nazwa punktu ustawień niestandardowych.<br /><br /> W przypadku implementacji opartych na MPF nazwa klucza jest uzyskiwana przez połączenie `categoryName` argumentów i `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktora do `categoryName_objectName` .<br /><br /> Klucz może być pusty lub może zawierać identyfikator odwołania do zlokalizowanego ciągu w satelickiej bibliotece DLL. Ta wartość jest uzyskiwana z `objectNameResourceID` argumentu do <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktora. |
| Pakiet | REG_SZ | GUID | Identyfikator GUID pakietu VSPackage, który implementuje punkt ustawień niestandardowych.<br /><br /> Implementacje oparte na MPF za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasy, należy użyć `objectType` argumentu konstruktora zawierającego pakietu VSPackage <xref:System.Type> i odbicie w celu uzyskania tej wartości. |
| Kategoria | REG_SZ | GUID | Identyfikator GUID identyfikujący kategorię ustawień.<br /><br /> W przypadku implementacji opartych na zestawach międzyoperacyjnych ta wartość może być wybranym przez siebie identyfikatorem GUID, który [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE przechodzi do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metody i. Wszystkie implementacje tych dwóch metod powinny weryfikować ich argumenty GUID.<br /><br /> W przypadku implementacji opartych na MPF ten identyfikator GUID jest uzyskiwany przez <xref:System.Type> klasę implementującą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mechanizm ustawień. |
| ResourcePackage | REG_SZ | GUID | Opcjonalny.<br /><br /> Ścieżka do satelickiej biblioteki DLL zawierającej zlokalizowane ciągi, jeśli implementacja pakietu VSPackage nie dostarcza tych plików.<br /><br /> MPF używa odbicia w celu uzyskania poprawnego pakietu VSPackage zasobu, więc <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Klasa nie ustawia tego argumentu. |
| AlternateParent | REG_SZ | Nazwa folderu na stronie Opcje narzędzi zawierające ten punkt ustawień niestandardowych. | Opcjonalny.<br /><br /> Należy ustawić tę wartość tylko wtedy, gdy implementacja ustawień obsługuje strony **opcji narzędzi** , które używają mechanizmu trwałości [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] zamiast mechanizmu w modelu automatyzacji do zapisywania stanu.<br /><br /> W takich przypadkach wartość w kluczu AlternateParent jest `topic` sekcją `topic.sub-topic` ciągu służącą do identyfikowania określonej strony **ToolsOptions** . Na przykład dla strony **ToolsOptions** `"TextEditor.Basic"` wartość AlternateParent byłaby równa `"TextEditor"` .<br /><br /> Podczas <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generowania punktu ustawień niestandardowych jest taka sama jak nazwa kategorii. |
