---
title: CATID dla obiektów zwykle używanych do rozszerania projektów
description: Poznaj CATID dla obiektów, które są używane do rozszerania obiektów automatyzacji projektu i ProjectItem dla Visual Basic, Visual C# i Visual C++ projektów.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1b0b20425cd1508db29932e9687d00055e4db58c
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190021"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>CATID dla obiektów, które są zwykle używane do rozszerania projektów
Poniższa tabela zawiera listę CATID, które służą do rozbudowywania `Project` i `ProjectItem` automatyzacji obiektów dla [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] . Te CATID są zdefiniowane w *VSLangProj. olb*.

## <a name="listing-of-catids"></a>Lista CATID

|Nazwa|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>Visual Basic CATID
 Poniższa tabela zawiera listę CATID, które są używane do rozszerania [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] obiektów do przeglądania. Wszystkie te definicje są zdefiniowane w *VSLangProj. olb*.

|Nazwa|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>Visual C# CATID
 Poniższe CATID mogą służyć do rozszerania [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] przeglądania obiektów. Wszystkie te definicje są zdefiniowane w *VSLangProj. olb*.

|Nazwa|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C++ CATID
 Następujące [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID systemu projektu nie są ujawniane w bibliotekach typów w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 i muszą być dołączone do kodu za każdym razem, gdy chcesz rozłożyć te obiekty projektu. Te CATID zostaną uwzględnione w bibliotekach typów w nowszych wersjach programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nazwa|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 Poniższy przykład kodu demonstruje, jak programować te CATID w kodzie.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Następujące [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] CATID systemu projektu nie są również ujawniane w bibliotekach typów w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .NET 2003 i muszą być dołączone do kodu za każdym razem, gdy chcesz rozłożyć te obiekty projektu. Te CATID są dostępne tylko w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .net 2003 i nie będą dostępne w nowszych wersjach programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

|Nazwa|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 Poniższy przykład kodu demonstruje, jak programować te CATID w kodzie:

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 Identyfikatory GUID dla [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] typów projektów i są przedstawione w poniższej tabeli.

| Project type (Typ projektu) | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>Zobacz też
- [Dodaj projekty i szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Rejestruj szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)
