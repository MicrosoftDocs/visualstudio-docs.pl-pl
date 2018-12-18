---
title: Implementowanie kolorowania składni | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a53b1fc04bd08835ccf0ff0b0edb2e5d117fcb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51775033"
---
# <a name="implementing-syntax-coloring"></a>Implementowanie kolorowania składni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy usługa językowa udostępnia kolorowania składni, analizator konwertuje tablicę elementów z możliwością kolorowania wiersza tekstu i zwraca typy tokenów odpowiadający te elementy z możliwością kolorowania. Analizator powinien zwrócić typy tokenów, które należą do listy elementów z możliwością kolorowania. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Wyświetla każdy element z możliwością kolorowania w oknie kodu według atrybutów przypisanych przez obiekt colorizer do odpowiedniego typu tokenu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nie określono interfejsu analizatora, i wykonania parser zależy od całkowicie użytkownika. Jednak domyślna implementacja parser znajduje się w projekcie pakiet językowy Visual Studio. Dla kodu zarządzanego środowiska pakietu zarządzanego (MPF) zapewnia pełną obsługę Kolorowanie tekstu.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie Implementowanie kolorowania składni, zobacz [przewodnik: wyróżnianie tekstu](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Kroki następuje edytor, którego można kolorować tekstu  
  
1.  Edytor pobiera colorizer, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> obiektu.  
  
2.  Wywołania edytora <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> metodę, aby ustalić, czy colorizer wymaga stanu każdego wiersza, aby zachować poza colorizer.  
  
3.  Jeśli colorizer wymaga stanu, aby zachować poza colorizer, Edytor wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> metodę, aby uzyskać stan pierwszego wiersza.  
  
4.  Dla każdego wiersza w buforze wywołuje edytora <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody, która wykonuje następujące czynności:  
  
    1.  Wiersz tekstu jest przekazywany do skanera do konwertowania tekstu na tokeny. Każdy token Określa tekst tokenu i typ tokenu.  
  
    2.  Typ tokenu jest konwertowany na indeks listy elementów z możliwością kolorowania.  
  
    3.  Dane tokenu jest używany do wypełnienia w tablicy w taki sposób, że każdy element tablicy odnosi się do znaku w wierszu. Wartości przechowywane w tablicy są indeksów do listy elementów z możliwością kolorowania.  
  
    4.  Stan na końcu wiersza jest zwracany w każdym wierszu.  
  
5.  Jeśli colorizer wymaga stanu, aby zachować, Edytor buforuje stan dla tej linii.  
  
6.  Edytor powoduje wyświetlenie wiersza tekstu przy użyciu informacje zwrócone ze <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metody. Wymagane jest wykonanie następujących kroków:  
  
    1.  Dla każdego znaku w wierszu uzyskać indeks z możliwością kolorowania elementu.  
  
    2.  Przy użyciu elementów z możliwością kolorowania domyślne, należy uzyskać dostęp do listy elementów z możliwością kolorowania edytora.  
  
    3.  W przeciwnym razie wywołanie usługi językowej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> metodę, aby uzyskać element z możliwością kolorowania.  
  
    4.  Skorzystaj z informacji w elemencie z możliwością kolorowania do renderowania tekstu do wyświetlania.  
  
## <a name="managed-package-framework-colorizer"></a>Colorizer Framework zarządzanego pakietu  
 Środowiska pakietu zarządzanego (MPF) udostępnia wszystkie klasy, które są wymagane do zaimplementowania colorizer. Powinien dziedziczyć klasy usługi języka <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i wdrożyć wymagane metody. Należy podać skanera i analizatora, implementując <xref:Microsoft.VisualStudio.Package.IScanner> interfejs i zwrócenia wystąpienia interfejsu z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> — metoda (jednej z metod, które muszą zostać zaimplementowane w <xref:Microsoft.VisualStudio.Package.LanguageService> klasy). Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: używanie wbudowanych elementów z możliwością kolorowania](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Niestandardowe elementy z możliwością kolorowania](../../extensibility/internals/custom-colorable-items.md)   
 [Tworzenie starszej wersji usługi językowej](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

