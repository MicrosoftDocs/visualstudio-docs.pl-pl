---
title: Implementowanie starszej wersji usługi językowej1 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436109"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Klas środowiska pakietu zarządzanego (MPF) można użyć do wdrożenia usługi starszego języka, który obsługuje szeroką gamę funkcji, takich jak wyróżnianie składni, parowanie nawiasów klamrowych i uzupełnianie przez funkcję IntelliSense.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji usługi języka, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)  
 Omówienie funkcji usługi języka, które są obsługiwane w MPF.  
  
 [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 W tym artykule opisano, co jest wymagane do wdrożenia usługi językowej przy użyciu MPF.  
  
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 W tym artykule opisano kroki, które są wymagane do zarejestrowania usługi języka opartego na MPF z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 W tym artykule opisano dwa analizatory składni, które są wymagane do wdrożenia wszystkich funkcji wersji usługi językowej przy użyciu MPF.  
  
 [Przewodnik: tworzenie starszej wersji usługi językowej](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Zawiera podstawowe kroki, które są wymagane do wdrożenia usługi w języka MPF w VSPackage.  
  
 [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Pokazuje technik pobieranie listy zainstalowanych fragmentów kodu.  
  
 [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)  
 Zawiera łącza do tematów w tym szczegółów, co należy zrobić, aby zaimplementować wszystkie funkcje usługi w języka przy użyciu MPF.
