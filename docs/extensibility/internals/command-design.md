---
title: Projekt polecenia | Microsoft Docs
description: Dowiedz się, jak zaprojektować polecenie dla pakietu VSPackage w programie Visual Studio. W tym, jak określić, gdzie pojawia się, gdy jest dostępny, oraz jak ma być obsługiwane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ab06ade9be1ccd0683cd298a5e758ddcfa883f8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304865"
---
# <a name="command-design"></a>Projekt polecenia
Po dodaniu polecenia do pakietu VSPackage należy określić, gdzie ma być wyświetlana, gdy jest dostępne, oraz jak ma być obsługiwane.

## <a name="define-commands"></a>Definiuj polecenia
 Aby zdefiniować nowe polecenia, należy dołączyć plik tabeli programu Visual Studio (*. vsct*) do projektu pakietu VSPackage. Jeśli utworzono pakietu VSPackage za pomocą szablonu pakietu programu Visual Studio, projekt zawiera jeden z tych plików. Aby uzyskać więcej informacji, zobacz [pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Program Visual Studio scala wszystkie znalezione pliki *. vsct* , aby umożliwić wyświetlanie poleceń. Ponieważ te pliki różnią się od pliku binarnego pakietu VSPackage, program Visual Studio nie musi ładować pakietu, aby znaleźć polecenia. Aby uzyskać więcej informacji, zobacz [jak pakietów VSPackage dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Program Visual Studio używa <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atrybutu rejestracji do definiowania zasobów menu i poleceń. Aby uzyskać więcej informacji, zobacz [implementacja poleceń](../../extensibility/internals/command-implementation.md).

 Polecenia można zmieniać w czasie wykonywania na wiele różnych sposobów. Mogą być wyświetlane lub ukrywane, włączane lub wyłączane. Mogą wyświetlać różne teksty lub ikony lub zawierać różne wartości. Aby program Visual Studio ładował Twoje pakietu VSPackage, można wykonać bardzo wiele operacji dostosowywania. Aby uzyskać więcej informacji, zobacz [jak pakietów VSPackage dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Programy obsługi poleceń
 Podczas tworzenia polecenia należy podać procedurę obsługi zdarzeń, aby wykonać polecenie. Jeśli użytkownik wybierze polecenie, musi być odpowiednio rozesłane. Kierowanie polecenia oznacza wysłanie go do odpowiedniej pakietu VSPackage, aby włączyć lub wyłączyć go, ukryć lub wyświetlić, a następnie wykonać, jeśli użytkownik zdecyduje się to zrobić. Aby uzyskać więcej informacji, zobacz [algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Środowisko poleceń programu Visual Studio
 Program Visual Studio może obsługiwać dowolną liczbę pakietów VSPackage, a każdy z nich może współtworzyć własny zestaw poleceń. Środowisko wyświetla tylko te polecenia, które są odpowiednie dla bieżącego zadania. Aby uzyskać więcej informacji, zobacz [dostępność poleceń](../../extensibility/internals/command-availability.md) i [obiekty kontekstu wyboru](../../extensibility/internals/selection-context-objects.md).

 Pakietu VSPackage, który definiuje nowe polecenia, menu, paski narzędzi lub menu skrótów, zawiera informacje o poleceniach do programu Visual Studio podczas instalacji za pomocą wpisów rejestru, które odwołują się do zasobów w zestawach natywnych lub zarządzanych. Każdy zasób odwołuje się do pliku zasobów danych binarnych (*dyrektor ds*), który jest tworzony podczas kompilowania pliku tabeli poleceń programu Visual Studio (*. vsct*). Dzięki temu program Visual Studio może udostępniać scalone zestawy poleceń, menu i paski narzędzi bez konieczności ładowania wszystkich zainstalowanych pakietu VSPackage.

### <a name="command-organization"></a>Organizacja poleceń
 Środowisko określa polecenia według grup, priorytetów i menu.

- Grupy są logicznymi kolekcjami powiązanych poleceń, na przykład z grupą poleceń **wycinania**, **kopiowania** i **wklejania** . Grupy są poleceniami, które pojawiają się w menu.

- Priorytet określa kolejność, w jakiej poszczególne polecenia w grupie pojawiają się w menu.

- Menu pełnią rolę kontenerów dla grup.

  Środowisko wstępnie definiuje niektóre polecenia, grupy i menu. Aby uzyskać więcej informacji, zobacz [domyślne umieszczanie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Polecenie można przypisać do grupy podstawowej. Grupa podstawowa kontroluje położenie polecenia w strukturze menu głównego i w oknie dialogowym **Dostosuj** . Polecenie może pojawić się w wielu grupach; na przykład polecenie może być w menu głównym, w menu skrótów i na pasku narzędzi. Aby uzyskać więcej informacji, zobacz [jak pakietów VSPackage dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Routing poleceń
 Proces wywoływania poleceń i routingu dla pakietów VSPackage różni się od procesu wywoływania metod w wystąpieniach obiektów.

 Środowisko kieruje polecenia sekwencyjnie od wewnętrznego kontekstu poleceń (lokalnego), który jest oparty na bieżącym zaznaczeniu, do zewnętrznego kontekstu (globalnego). Pierwszy kontekst, który jest w stanie wykonać polecenie, jest taki, który go obsługuje. Aby uzyskać więcej informacji, zobacz [algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md).

 W większości przypadków środowisko obsługuje polecenia przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Ze względu na to, że schemat routingu poleceń umożliwia wiele różnych obiektów do obsługi poleceń, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> może być zaimplementowany przez dowolną liczbę obiektów. obejmują one kontrolki ActiveX firmy Microsoft, implementacje widoku okna, obiekty dokumentów, hierarchie projektu i same obiekty pakietu VSPackage (dla poleceń globalnych). W niektórych wyspecjalizowanych przypadkach, na przykład poleceń routingu w hierarchii, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> należy zaimplementować interfejs.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Implementacja polecenia](../../extensibility/internals/command-implementation.md)|Opisuje sposób implementacji poleceń w pakietu VSPackage.|
|[Dostępność polecenia](../../extensibility/internals/command-availability.md)|Opisuje, w jaki sposób kontekst programu Visual Studio Określa, które polecenia są dostępne.|
|[Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md)|Opisuje sposób, w jaki architektura routingu poleceń programu Visual Studio umożliwia obsługę poleceń przez różne pakietów VSPackage.|
|[Wskazówki dotyczące umieszczania poleceń](../../extensibility/internals/command-placement-guidelines.md)|Sugeruje sposób pozycjonowania poleceń w środowisku programu Visual Studio.|
|[Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Opisuje, jak pakietów VSPackage może najlepiej wykorzystać architekturę poleceń programu Visual Studio.|
|[Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Opisuje, jak pakietów VSPackage może najlepiej korzystać z poleceń, które są zawarte w programie Visual Studio.|
|[Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)|Opisuje, jak program Visual Studio ładuje pakietów VSPackage.|
|[Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Zawiera informacje o plikach *vsct* opartych na języku XML, które są używane do opisywania układu i wyglądu poleceń w pakietów VSPackage.|
