---
title: Obsługa ustawień użytkownika | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704788"
---
# <a name="support-for-user-settings"></a>Pomoc techniczna dotycząca ustawień użytkownika
VsPackage może zdefiniować jedną lub więcej kategorii ustawień, które są grupami zmiennych stanu, które utrzymują się, gdy użytkownik wybierze polecenie **Import/Eksportuj ustawienia** w menu **Narzędzia.** Aby włączyć tę trwałość, należy użyć ustawień [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]interfejsów API w pliku .

 Wpis rejestru, który jest określany jako punkt ustawień niestandardowych i identyfikator GUID definiuje kategorię ustawień VSPackage. VsPackage może obsługiwać wiele kategorii ustawień, z których każda jest zdefiniowana przez punkt ustawień niestandardowych.

- Implementacje ustawień, które są oparte na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> zestawach interop (przy użyciu interfejsu) należy utworzyć Punkt ustawień niestandardowych przez edycję rejestru lub przy użyciu skryptu rejestratora (plik rgs). Aby uzyskać więcej informacji, zobacz [Tworzenie skryptów rejestratora](/cpp/atl/creating-registrar-scripts).

- Kod, który używa struktury pakietu zarządzanego (MPF) należy <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> utworzyć punkty ustawień niestandardowych, dołączając do VSPackage dla każdego punktu ustawień niestandardowych.

     Jeśli pojedynczy VSPackage obsługuje kilka punktów ustawień niestandardowych, każdy punkt ustawień niestandardowych jest implementowany <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> przez oddzielną klasę, a każdy jest zarejestrowany przez unikatowe wystąpienie klasy. W związku z tym ustawienia implementujące klasę może obsługiwać więcej niż jedną kategorię ustawień.

## <a name="custom-settings-point-registry-entry-details"></a>Szczegóły wpisu rejestru punktu ustawień niestandardowych
 Niestandardowe punkty ustawień są tworzone we wpisie rejestru w następującej lokalizacji:\\HKLM\Software\Microsoft\VisualStudio `<CSPName>` *\<Version>* \UserSettings\\`<CSPName>`, gdzie jest nazwa punktu ustawień [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]niestandardowych obsługują vspackage i * \<>wersji* jest wersją , na przykład 8.0.

> [!NOTE]
> Ścieżka główna HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* może zostać zastąpiona alternatywnym katalogiem głównym [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] po zainicjowaniu zintegrowanego środowiska programistycznego (IDE). Aby uzyskać więcej informacji, zobacz [Przełączniki wiersza polecenia](../../extensibility/command-line-switches-visual-studio-sdk.md).

 Struktura wpisu rejestru jest zilustrowana poniżej:

 HKLM\Software\Microsoft\VisualStudio\\*\<Version>* \UserSettings\

 `<CSPName`>= s '#12345'

 Pakiet = '{XXXXXX XXXX XXXX XXXX XXXXXXXXXXX}'

 Kategoria = '{YYYYYYY YYYYY YYYYY YYYYY YYYYYYYYYYY}'

 Pakiet zasobów = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = Nazwa kategorii

| Nazwa | Typ | Dane | Opis |
|-----------------|--------| - | - |
| (Domyślnie) | REG_SZ | Nazwa punktu ustawień niestandardowych | Nazwa klucza, `<CSPName`>, jest nieprzydzieloną nazwą punktu ustawień niestandardowych.<br /><br /> W przypadku implementacji opartych na mpf nazwa klucza `categoryName` `objectName` jest uzyskiwana przez połączenie argumentów i argumentów <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> konstruktora w `categoryName_objectName`.<br /><br /> Klucz może być pusty lub może zawierać identyfikator odniesienia do zlokalizowanego ciągu w satelicie DLL. Ta wartość jest `objectNameResourceID` uzyskiwana z argumentu do konstruktora. <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> |
| Pakiet | REG_SZ | Identyfikator GUID | Identyfikator GUID programu VSPackage, który implementuje punkt ustawień niestandardowych.<br /><br /> Implementacje oparte na <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> MPF przy użyciu klasy, należy użyć argumentu `objectType` <xref:System.Type> konstruktora zawierającego VSPackage i odbicia, aby uzyskać tę wartość. |
| Kategoria | REG_SZ | Identyfikator GUID | Identyfikator GUID identyfikujący kategorię ustawień.<br /><br /> Dla implementacji opartych na zestawach międzyoperacyjnych ta wartość może być [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dowolnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> wybrany <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> identyfikator GUID, który IDE przechodzi do i metody. Wszystkie implementacje tych dwóch metod należy zweryfikować ich argumenty GUID.<br /><br /> Dla implementacji opartych na MPF ten <xref:System.Type> identyfikator GUID jest [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uzyskiwany przez klasę implementującą mechanizm ustawień. |
| Pakiet zasobów | REG_SZ | Identyfikator GUID | Element opcjonalny.<br /><br /> Ścieżka do biblioteki DLL satelity zawierającej zlokalizowane ciągi, jeśli implementująca usługa VSPackage ich nie dostarcza.<br /><br /> MPF używa odbicia w celu uzyskania odpowiedniego zasobu VSPackage, więc <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> klasa nie ustawia tego argumentu. |
| Zastępca rodzica | REG_SZ | Nazwa folderu na stronie Opcje narzędzi zawierającej ten punkt ustawień niestandardowych. | Element opcjonalny.<br /><br /> Tę wartość należy ustawić tylko wtedy, gdy implementacja ustawień obsługuje [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] strony **Opcje narzędzi,** które używają mechanizmu trwałości w zamiast mechanizmu w modelu automatyzacji, aby zapisać stan.<br /><br /> W takich przypadkach wartość w AlternateParent `topic` klucz jest `topic.sub-topic` sekcja ciągu używane do identyfikowania **poszczególnych ToolsOptions** strony. Na przykład dla **toolsoptions** strony `"TextEditor.Basic"` wartość AlternateParent `"TextEditor"`będzie .<br /><br /> Gdy <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> generuje punkt ustawień niestandardowych, jest taka sama jak nazwa kategorii. |
