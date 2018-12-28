---
title: PreviewImage, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 313f97324d3b4eed5a9d0866bef94ee9265701eb
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562051"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage, element (szablony Visual Studio)
Określa obraz podglądu jako nazwę pliku dla obrazu podglądu, która będzie wyświetlana w jednym **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<PreviewImage >  
  
## <a name="syntax"></a>Składnia  
  
```  
<PreviewImage>"filename"</PreviewImage>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być ciągiem, który reprezentuje nazwę pliku.  
  
## <a name="remarks"></a>Uwagi  
 `PreviewImage` element jest opcjonalny.  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)