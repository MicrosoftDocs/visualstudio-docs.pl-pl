---
title: Tabela poleceń programu Visual Studio (. Vsct) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cde3b86e19788c41df6e8f1c79a6bf829f491170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675247"
---
# <a name="visual-studio-command-table-vsct-files"></a>Tabela poleceń programu Visual Studio (pliki Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Plik konfiguracji tabeli poleceń to plik tekstowy, który opisuje zestaw poleceń, które zawiera pakietu VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Kompilator Command Table (vsct) kompiluje pliki konfiguracyjne oparte na języku XML (pliki. vsct) do plików wyjściowych tabeli poleceń binarnych (. Dyrektor ds). Wynikowe pliki dyrektor ds są takie same jak te, które są tworzone za pomocą kompilatora Command Table (CTC), do kompilowania plików konfiguracji CTC. Jednak pliki vsct oparte na języku XML mają pewne zalety, takie jak Edytor XML i IntelliSense XML.  
  
 Aby dowiedzieć się więcej na temat składni i semantyki plików. vsct, zobacz [Designing XML Command Table (. Vsct) — pliki](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projektowanie tabeli poleceń XML (pliki Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Opisuje sposób projektowania plików. vsct.  
  
 [Instrukcje: tworzenie pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Porównuje metody tworzenia pliku. vsct. Opisuje proces ręcznego tworzenia nowego pliku. vsct.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Zawiera szczegółowe informacje o każdej sekcji pliku konfiguracyjnego XML tabeli poleceń.  
  
 [Konfiguracja tabeli poleceń (. CTC) — pliki](https://msdn.microsoft.com/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Przedstawia Omówienie przestarzałego formatu pliku. CTC.  
  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Opisuje specyfikację formatu tabeli poleceń.  
  
 [Zasoby w pakietach VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Opisuje sposób używania zasobów zarządzanych i niezarządzanych w zarządzanych pakietów VSPackage.  
  
 [Polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Wyjaśnia, jak utworzyć interfejs użytkownika, który obejmuje menu, paski narzędzi i pola kombi poleceń.
