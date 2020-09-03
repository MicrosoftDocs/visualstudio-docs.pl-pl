---
title: Starsze interfejsy w edytorze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy
ms.assetid: 741d45f5-0ea3-4614-972a-8728fe054e07
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8483068ae03c9a57fc67b528393e5d6830c3ec33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180292"
---
# <a name="legacy-interfaces-in-the-editor"></a>Starsze interfejsy w edytorze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz uzyskać dostęp do edytora programu Visual Studio ze starszych interfejsów. Zestaw Visual Studio SDK zawiera karty znane jako *podkładki*, które umożliwiają współdziałanie tych interfejsów z nowym edytorem. Niemniej jednak zalecamy zaktualizowanie starszego kodu, aby korzystał z nowego interfejsu API edytora. Kod będzie działać lepiej i można używać nowych technologii, takich jak Windows Presentation Foundation (WPF) i Managed Extensibility Framework (MEF).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Dostosowanie starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|Wyjaśnia, jak dostosować kod do nowego edytora.|  
|[Nowe lub zmienione działanie z użyciem adapterów edytora](../extensibility/new-or-changed-behavior-with-editor-adapters.md)|Wyjaśnia, jak zachowanie kart edytora różni się od wcześniejszej wersji edytora.|  
|[Wewnątrz edytora podstawowego](../extensibility/inside-the-core-editor.md)|Opisuje różne składniki wcześniejszych wersji edytora.|  
|[Tworzenie wystąpienia edytora podstawowego przy użyciu starszej wersji interfejsu API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)|Wyjaśnia, jak używać starszego interfejsu API do tworzenia wystąpienia podstawowego edytora.|  
|[Fabryki edytorów](../extensibility/editor-factories.md)|Wyjaśnia, jak używać fabryk edytora ze starszym interfejsem API.|  
|[Instrukcje: rejestrowanie typów plików edytora](../extensibility/how-to-register-editor-file-types.md)|Wyjaśnia, jak połączyć rozszerzenie nazwy pliku z edytorem.|  
|[Przewodnik: tworzenie edytora podstawowego i rejestrowanie typu pliku edytora](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)|Wyjaśnia, jak utworzyć podstawowy edytor i połączyć z nim rozszerzenie nazwy pliku.|  
|[Instrukcje: dostarczanie kontekstu edytorom](../extensibility/how-to-provide-context-for-editors.md)|Wyjaśnia, jak zapewnić kontekst dla edytora.|  
|[Usługi językowe oraz edytor podstawowy](../extensibility/language-services-and-the-core-editor.md)|Wyjaśnia interakcje między usługą języka a edytorem.|  
|[Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)|Wyjaśnia, jak uzyskać dostęp do buforu tekstowego przy użyciu starszego interfejsu API.|  
|[Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)|Wyjaśnia, jak uzyskać dostęp do widoku tekstu przy użyciu starszego interfejsu API.|  
|[Dostosowywanie okien kodu za pomocą starszego interfejsu API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)|Wyjaśnia, jak dostosować okna kodu przy użyciu starszego interfejsu API.|  
|[Uzyskiwanie dostępu do warstw tekstu za pomocą starszego interfejsu API](../extensibility/accessing-text-layers-by-using-the-legacy-api.md)|Wyjaśnia, jak uzyskać dostęp do różnych warstw tekstu przy użyciu starszego interfejsu API.|  
|[Korzystanie ze znaczników tekstu ze starszym interfejsem API](../extensibility/using-text-markers-with-the-legacy-api.md)|Wyjaśnia, jak dodać znaczniki tekstu przy użyciu starszego interfejsu API.|  
|[Dostosowywanie kontrolek i menu w edytorze za pomocą starszego interfejsu API](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)|Wyjaśnia, jak dostosować formanty edytora przy użyciu starszego interfejsu API.|  
|[Zarządzanie cofaniem i ponawianiem przy użyciu starszego interfejsu API](../extensibility/managing-undo-and-redo-by-using-the-legacy-api.md)|Wyjaśnia, jak zarządzać Cofnij i ponownie za pomocą starszego interfejsu API.|  
|[Instrukcje: implementowanie mechanizmu znajdowania i zamieniania](../extensibility/how-to-implement-the-find-and-replace-mechanism.md)|Wyjaśnia sposób zarządzania Znajdowanie i zamienianie przy użyciu starszego interfejsu API.|  
|[Instrukcje: pomijanie powiadomienia o zmianie pliku](../extensibility/how-to-suppress-file-change-notifications.md)|Wyjaśnia, jak pominąć powiadomienia o zmianie plików przy użyciu starszego interfejsu API.|  
|[Tworzenie niestandardowych edytorów i projektantów](../extensibility/creating-custom-editors-and-designers.md)|Wyjaśnia, jak tworzyć edytory niestandardowe i projektantów.|  
|[Tworzenie starszej wersji usługi językowej](../extensibility/internals/developing-a-legacy-language-service.md)|Zawiera łącza do dokumentów dotyczących funkcji, które udostępniają możliwości dostosowywania do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edytora podstawowego przez dodanie obsługi usługi językowej.|  
|[Korzystanie z czcionek i kolorów](../extensibility/using-fonts-and-colors.md)|Wyjaśnia, jak używać czcionek i kolorów ze starszymi interfejsami.|
