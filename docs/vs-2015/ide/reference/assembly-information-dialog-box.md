---
title: Informacje o zestawie — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661027"
---
# <a name="assembly-information-dialog-box"></a>Informacje o zestawie — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Okno dialogowe **Informacje o zestawie** służy do określania wartości [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] globalnych atrybutów zestawu, które są przechowywane w pliku AssemblyInfo tworzonym automatycznie przy użyciu projektu. W **Eksplorator rozwiązań**, plik znajduje się w węźle **My Project** w [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (kliknij przycisk **Pokaż wszystkie pliki** , aby go wyświetlić); znajduje się w obszarze **Właściwości** w [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Aby uzyskać więcej informacji o atrybutach zestawu, zobacz [atrybuty](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Aby uzyskać dostęp do tego okna dialogowego, wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **aplikacja** . Na stronie **aplikacja** kliknij przycisk **Informacje o zestawie** .

## <a name="uielement-list"></a>Lista elementów UI
 **Tytuł** Określa tytuł manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTitleAttribute> .

 **Opis** Określa opcjonalny opis manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyDescriptionAttribute> .

 **Firma** Określa nazwę firmy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCompanyAttribute> .

 **Produkt** Określa nazwę produktu dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyProductAttribute> .

 **Prawa autorskie** Określa informacje o prawach autorskich dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyCopyrightAttribute> .

 **Znak towarowy** Określa znak towarowy dla manifestu zestawu. Odnosi się do <xref:System.Reflection.AssemblyTrademarkAttribute> .

 **Wersja zestawu** Określa wersję zestawu. Odnosi się do <xref:System.Reflection.AssemblyVersionAttribute> .

 **Wersja pliku** Określa numer wersji, który instruuje kompilator, aby używał określonej wersji dla zasobu wersji plików Win32. Odnosi się do <xref:System.Reflection.AssemblyFileVersionAttribute> .

 **Identyfikator GUID** Unikatowy identyfikator GUID, który identyfikuje zestaw. Podczas tworzenia projektu program Visual Studio generuje identyfikator GUID dla zestawu. Odnosi się do <xref:System.Guid> .

 **Język neutralny** Określa kulturę obsługiwaną przez zestaw. Odnosi się do <xref:System.Resources.NeutralResourcesLanguageAttribute> . Wartość domyślna to **(brak)**.

 **Ustaw zestaw com jako widoczny** Określa, czy typy w zestawie będą dostępne dla modelu COM. Odnosi się do <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

## <a name="see-also"></a>Zobacz też
 [Strona aplikacji, Projektant projektu (Visual Basic) —](../../ide/reference/application-page-project-designer-visual-basic.md) [atrybuty](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
