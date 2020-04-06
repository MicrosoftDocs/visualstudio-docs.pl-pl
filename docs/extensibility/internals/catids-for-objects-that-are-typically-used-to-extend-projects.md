---
title: CATID dla obiektów, które są zwykle używane do rozszerzania projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5754e53f24731eb44dba128ccfcf4b474e833d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709867"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>Catidy dla obiektów, które są zwykle używane do rozszerzania projektów
W poniższej tabeli wymieniono identyfikatory `Project` `ProjectItem` CATID, które są używane do rozszerzania i automatyzacji obiektów dla [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]programów [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów. Te identyfikatory CATID są zdefiniowane w *pliku VSLangProj.olb*.

## <a name="listing-of-catids"></a>Lista CATIDs

|Nazwa|Identyfikator GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATIDs
 W poniższej tabeli wymieniono identyfikatory [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] CATID, które są używane do rozszerzania obiektów przeglądania. Wszystkie są zdefiniowane w *pliku VSLangProj.olb*.

|Nazwa|Identyfikator GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Wizualne identyfikatory CATID w języku C#
 Do rozszerzania [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] obiektów przeglądania można użyć następujących identyfikatorów CATID. Wszystkie są zdefiniowane w *pliku VSLangProj.olb*.

|Nazwa|Identyfikator GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C++ CATIDs
 Następujące [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] identyfikatory CATID systemu projektu nie są [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] widoczne w bibliotekach typów w programie .NET 2003 i muszą być uwzględnione w kodzie, gdy chcesz rozszerzyć te obiekty projektu. Te identyfikatory CATID zostaną uwzględnione w bibliotekach [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]typów w późniejszych wersjach .

|Nazwa|Identyfikator GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Poniższy przykład kodu pokazuje, jak zaprogramować te identyfikatory CATID w kodzie.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Następujące [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] identyfikatory CATID systemu projektu nie są również [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] widoczne w bibliotekach typów w programie .NET 2003 i muszą być uwzględnione w kodzie, gdy chcesz rozszerzyć te obiekty projektu. Te identyfikatory CATID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są dostępne tylko w .NET 2003 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]i nie będą dostępne w późniejszych wersjach .

|Nazwa|Identyfikator GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Poniższy przykład kodu pokazuje, jak zaprogramować te identyfikatory CATID w kodzie:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Identyfikatory GUID [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dla [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typów i projektu są pokazane w poniższej tabeli.

| Project type (Typ projektu) | Identyfikator GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Zobacz też
- [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Rejestrowanie szablonów projektów i towarów](../../extensibility/internals/registering-project-and-item-templates.md)
