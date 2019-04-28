---
title: Tworzenie starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 36ff8335bfaf99b5826d217a48910bfd581321e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440116"
---
# <a name="developing-a-legacy-language-service"></a>Tworzenie starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sekcja Łącze do tematów, które ułatwiają tworzenie starszej wersji usługi językowej.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Model starszej wersji usługi językowej](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Udostępnia model usługi minimalny języka na potrzeby [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] edytorze podstawowych funkcji. Ten model jako przewodnik służy do tworzenia usługi języka.  
  
 [Interfejsy starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Omówiono obiekty wymagane do wykonania usługi językowej i listę dodatkowe obiekty, które służy do wyróżniania składni, Metoda danych i innych funkcji.  
  
 [Przechwytywanie poleceń starszej wersji usługi językowej](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Opisuje sposób wstawić filtr polecenia do usługi języka do poleceń intercept, które widoku tekstu w przeciwnym razie będzie obsługiwać.  
  
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Zawiera informacje o tym, jak zarejestrować usługi w języka przy użyciu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Obsługa usługi językowej do debugowania](../../extensibility/internals/language-service-support-for-debugging.md)  
 W tym artykule opisano, jak usługa języka może zapewnić funkcji obsługi debugera.  
  
 [Lista kontrolna: tworzenie starszej wersji usługi językowej](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Instrukcje krok po kroku dotyczące tworzenia i integrowania usługi języka dla podstawowy edytor.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 W tym artykule omówiono sposób implementacji, wyróżnianie składni w usłudze języka.  
  
 [Uzupełnianie instrukcji w starszej wersji usługi językowej](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 W tym artykule omówiono uzupełniania instrukcji, proces, za pomocą którego usługa języka ułatwiają zakończyć słowem kluczowym języka lub element, który zostały uruchomione, wpisując.  
  
 [Informacje o parametrach w starszej wersji usługi językowej](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 W tym artykule opisano, jak zapewnić porady metodę dla przeciążonej funkcji i metod.  
  
 [Instrukcje: zapewnianie obsługi tekstu ukrytego w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Zawiera wyjaśnienie przeznaczenia obszaru tekstu ukrytego i zawiera instrukcje dotyczące sposobu implementacji region tekstu ukrytego.  
  
 [Instrukcje: zapewnianie rozszerzonej obsługi zwijania w starszej wersji usługi językowej](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Opisano dwie opcje, które rozszerzają obsługi zwijania dla danego języka, poza obsługi *Zwiń do definicji* polecenia.
