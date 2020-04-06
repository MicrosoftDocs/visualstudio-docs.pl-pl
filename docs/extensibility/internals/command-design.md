---
title: Projekt polecenia | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709661"
---
# <a name="command-design"></a>Projekt polecenia
Po dodaniu polecenia do VSPackage, należy określić, gdzie ma się pojawić, kiedy jest dostępny i jak ma być obsługiwany.

## <a name="define-commands"></a>Definiowanie poleceń
 Aby zdefiniować nowe polecenia, dołącz visual studio tabeli poleceń (*vsct*) plik w projekcie VSPackage. Jeśli utworzono VSPackage przy użyciu szablonu pakietu programu Visual Studio, projekt zawiera jeden z tych plików. Aby uzyskać więcej informacji, zobacz [Pliki tabeli poleceń programu Visual Studio (vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio scala wszystkie pliki *vsct,* które znajdzie, dzięki czemu można wyświetlić polecenia. Ponieważ te pliki różnią się od pliku binarnego VSPackage, visual studio nie musi ładować pakiet, aby znaleźć polecenia. Aby uzyskać więcej informacji, zobacz [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio używa <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atrybutu rejestracji do definiowania zasobów menu i poleceń. Aby uzyskać więcej informacji, zobacz [Implementacja polecenia](../../extensibility/internals/command-implementation.md).

 Polecenia można zmieniać w czasie wykonywania na wiele różnych sposobów. Mogą być wyświetlane lub ukryte, włączone lub wyłączone. Mogą wyświetlać inny tekst lub ikony lub zawierać różne wartości. Wiele dostosowywania można wykonać przed Visual Studio ładuje VSPackage. Aby uzyskać więcej informacji, zobacz [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Programy obsługi poleceń
 Podczas tworzenia polecenia, należy podać program obsługi zdarzeń, aby wykonać polecenie. Jeśli użytkownik wybierze polecenie, musi ono zostać odpowiednio rozesłane. Routing polecenia oznacza wysłanie go do właściwego vsPackage, aby włączyć lub wyłączyć go, ukryć lub wyświetlić go i wykonać go, jeśli użytkownik zdecyduje się to zrobić. Aby uzyskać więcej informacji, zobacz [Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Środowisko poleceń programu Visual Studio
 Visual Studio może obsługiwać dowolną liczbę vspackages i każdy może przyczynić się do własnego zestawu poleceń. Środowisko wyświetla tylko polecenia, które są odpowiednie dla bieżącego zadania. Aby uzyskać więcej informacji, zobacz [Dostępność polecenia](../../extensibility/internals/command-availability.md) i [obiekty kontekstu zaznaczenia](../../extensibility/internals/selection-context-objects.md).

 VsPackage, który definiuje nowe polecenia, menu, paski narzędzi lub menu skrótów udostępnia informacje o poleceniach programu Visual Studio w czasie instalacji za pośrednictwem wpisów rejestru, które odwołują się do zasobów w natywnych lub zarządzanych zestawach. Następnie każdy zasób odwołuje się do pliku binarnego zasobu danych (*.cto*), który jest produkowany podczas kompilowania pliku tabeli poleceń programu Visual Studio (*.vsct).* Dzięki temu visual studio, aby zapewnić scalone zestawy poleceń, menu i paski narzędzi bez konieczności ładowania co zainstalowany VSPackage.

### <a name="command-organization"></a>Organizacja poleceń
 Środowisko pozycjonuje polecenia według grupy, priorytetu i menu.

- Grupy są logicznymi kolekcjami pokrewnych poleceń, na przykład grupy poleceń **Wytnij,** **Kopiuj**i **Wklej.** Grupy to polecenia wyświetlane w menu.

- Priorytet określa kolejność, w jakiej poszczególne polecenia w grupie są wyświetlane w menu.

- Menu działają jako kontenery dla grup.

  Środowisko wstępnie domyślnie niektóre polecenia, grupy i menu. Aby uzyskać więcej informacji, zobacz [Domyślne polecenie, grupa i położenie paska narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Polecenie można przypisać do grupy podstawowej. Grupa podstawowa steruje położeniem polecenia w strukturze menu głównego i w oknie dialogowym **Dostosowywanie.** Polecenie może pojawić się w wielu grupach; na przykład polecenie może znajdować się w menu głównym, w menu skrótów i na pasku narzędzi. Aby uzyskać więcej informacji, zobacz [Jak VSPackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Routing poleceń
 Proces wywoływania i routingu poleceń dla VSPackages różni się od procesu wywoływania metod w wystąpieniach obiektów.

 Środowisko kieruje polecenia sekwencyjnie z najbardziej wewnętrznego (lokalnego) kontekstu polecenia, który jest oparty na bieżącym zaznaczeniu, do najbardziej zewnętrznego (globalnego) kontekstu. Pierwszy kontekst, który jest w stanie wykonać polecenie jest ten, który obsługuje go. Aby uzyskać więcej informacji, zobacz [Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md).

 W większości przypadków środowisko obsługuje polecenia przy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> użyciu interfejsu. Ponieważ schemat routingu poleceń umożliwia wiele <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> różnych obiektów do obsługi poleceń, mogą być implementowane przez dowolną liczbę obiektów; należą do nich formanty Microsoft ActiveX, implementacje widoku okien, obiekty dokumentu, hierarchie projektów i same obiekty VSPackage (dla poleceń globalnych). W niektórych wyspecjalizowanych przypadkach, na przykład, polecenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> routingu w hierarchii, interfejs musi być zaimplementowana.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Implementacja polecenia](../../extensibility/internals/command-implementation.md)|Opisuje sposób implementowania poleceń w programie VSPackage.|
|[Dostępność poleceń](../../extensibility/internals/command-availability.md)|W tym artykule opisano, jak kontekst programu Visual Studio określa, które polecenia są dostępne.|
|[Algorytm routingu poleceń](../../extensibility/internals/command-routing-algorithm.md)|W tym artykule opisano, jak architektura routingu poleceń programu Visual Studio umożliwia obsługę poleceń przez różne pakiety VSPackages.|
|[Wskazówki dotyczące umieszczania poleceń](../../extensibility/internals/command-placement-guidelines.md)|Sugeruje, jak umieścić polecenia w środowisku programu Visual Studio.|
|[Jak vspackages dodać elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|W tym artykule opisano, jak VSPackages najlepiej wykorzystać architekturę polecenia programu Visual Studio.|
|[Domyślne rozmieszczenie polecenia, grupy i paska narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|W tym artykule opisano, jak VSPackages najlepiej używać poleceń, które są zawarte w programie Visual Studio.|
|[Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)|W tym artykule opisano, jak visual studio ładuje vspackages.|
|[Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Zawiera informacje o plikach *vsct* opartych na języku XML, które są używane do opisywania układu i wyglądu poleceń w programie VSPackages.|
