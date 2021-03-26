---
title: Przegląd opcji konfiguracji | Microsoft Docs
description: Dowiedz się więcej na temat opcji konfiguracji projektu w programie Visual Studio. Konfiguracja jest typem kompilacji opisanym w nazwanym zestawie właściwości i lokalizacjami plików.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad30e3f7b91e8a76715f66d9f6701597f3830bd6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057133"
---
# <a name="configuration-options-overview"></a>Przegląd opcji konfiguracji
Projekty w programie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mogą obsługiwać wiele konfiguracji, które można kompilować, debugować, uruchamiać i/lub wdrażać. Konfiguracja jest typem kompilacji opisanym w nazwanym zestawie właściwości, zazwyczaj przełączników kompilatora i lokalizacjami plików. Domyślnie nowe rozwiązania zawierają dwie konfiguracje, *debugowanie* i *wydanie*. Te konfiguracje można zastosować przy użyciu ich ustawień domyślnych lub zmodyfikować w celu spełnienia określonych wymagań dotyczących rozwiązań i/lub projektu. Niektóre pakiety można utworzyć na dwa sposoby: jako edytor ActiveX lub jako składnik w miejscu. Projekty nie muszą jednak obsługiwać wielu konfiguracji. Jeśli dostępna jest tylko jedna konfiguracja, ta konfiguracja jest mapowana na wszystkie konfiguracje rozwiązań.

 Konfiguracje składają się zazwyczaj z dwóch części: nazwy konfiguracji (na przykład *Debug* lub *Release*) oraz ustawień platformy. Nazwa platformy konfiguracji identyfikuje środowisko, do którego należy Konfiguracja interfejsu API lub platformę systemu operacyjnego. Użytkownicy programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie mogą utworzyć platformy; muszą wybierać spośród wybranych opcji projektu pakietu VSPackage. Gdy użytkownik instaluje pakietu VSPackage, platforma dostarczania utworzona podczas opracowywania pakietu może posłużyć dowolną nazwę platformy w zależności od kryteriów ustawionych przez twórcę pakietu. Użytkownik może następnie wybrać z listy platform udostępnionych za pośrednictwem pakietu VSPackage, gdy zostanie utworzone wystąpienie stron właściwości.

 Nazwy platform są opcjonalne, ponieważ nie wszystkie projekty obsługują koncepcję platform. Jeśli konfiguracja nie ma nazwy platformy, ciąg **N/a** jest wyświetlany w interfejsie użytkownika.

 Każde rozwiązanie ma swój własny zestaw konfiguracji, tylko jeden z nich może być aktywny w danym momencie. Konfiguracja rozwiązania to zbiór nie więcej niż jednej konfiguracji z każdego projektu. Postanowienie "nie więcej niż" jest spowodowane opcją wykluczenia projektu z konfiguracji rozwiązania. Użytkownicy mogą tworzyć własne niestandardowe konfiguracje rozwiązań.

 W poniższej tabeli przedstawiono typowe ustawienia konfiguracji dla projektu. Wiersze są oznaczone etykietami z nazwami konfiguracji i kolumnami z nazwami platform.

|Nazwa konfiguracji|Platforma: Win32|Platforma: Win64|
|------------------------|----------------------|----------------------|
|*Debugowanie*|\<Debug Win32 settings>|\<Debug Win64 settings>|
|*Wersja*|\<Release Win32 settings>|\<Release Win64 settings>|
|*Mojakonfiguracja*|Nie dotyczy|\<MyConfig Win64 settings>|

> [!NOTE]
> Nie można utworzyć konfiguracji *rozwiązania z konfiguracją* , która wyklucza platformę Win32, chyba że docelowy projekt nie obsługuje Win32.

 Zmiana aktywnej konfiguracji rozwiązania powoduje wybranie zestawu konfiguracji projektu, które zostały skompilowane, uruchomione, debugowane lub wdrożone w tym rozwiązaniu. Na przykład w przypadku zmiany aktywnej konfiguracji rozwiązania z *wersji* na *Debuguj* wszystkie projekty w tym rozwiązaniu zostaną automatycznie skompilowane przy użyciu konfiguracji projektu wskazanej w konfiguracji debugowania rozwiązania. Konfiguracje projektów są również nazywane *debugowaniem* , chyba że użytkownik wprowadził ręcznie zmiany w Configuration Manager środowiska.

 Właściwości konfiguracji rozwiązania przechowywane dla każdego projektu obejmują nazwę projektu, nazwę konfiguracji projektu, flagi wskazujące, czy kompilacja lub wdrożenie oraz nazwa platformy. Aby uzyskać więcej informacji, zobacz temat [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

 Użytkownik może wyświetlać i ustawiać parametry konfiguracji rozwiązania, wybierając rozwiązanie w hierarchii (Eksplorator rozwiązań) i otwierając strony właściwości. Analogicznie, można wyświetlać i ustawiać parametry konfiguracji projektu, wybierając projekt w Eksplorator rozwiązań i otwierając strony właściwości dla tego projektu.

 Użytkownik może również utworzyć jeden projekt przy użyciu ustawień konfiguracji wydania oraz wszystkie pozostałe ustawienia konfiguracji debugowania, jeśli jest to konieczne. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md).

 Na poniższym diagramie przedstawiono sposób implementacji interfejsów, które obsługują konfiguracje rozwiązań i projektów:

 ![Grafika interfejsów konfiguracji](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfejsy konfiguracji

 Kilka notatek odnoszących się do poprzedniego diagramu:

- `IDispatch` jest oznaczona jako opcjonalna w obiekcie Configuration. W każdym przypadku opcjonalne jest posiadanie interfejsów konfiguracji w obiekcie Browse.

- `IVsDebuggableProjectCfg` jest oznaczona jako opcjonalna w obiekcie Configuration, ale jest wymagana do obsługi debugowania.

- `IVsProjectCfg2` jest oznaczona jako opcjonalna w obiekcie Configuration, ale jest wymagana w celu obsługi grupowania danych wyjściowych.

- Obiekt dostawcy konfiguracji jest oznaczony jako obiekt opcjonalny, ale jest to miejsce, w którym można go zaimplementować. Można zaimplementować obiekt w obiekcie projektu lub w oddzielnym obiekcie.

- `IVsCfgProvider2` jest wymagany do obsługi platformy i edytowania konfiguracji. `IVsCfgProvider` jest wystarczająca, jeśli ta funkcja nie zostanie wdrożona.

- Niektóre z tych obiektów pokazane na diagramie jako osobne obiekty mogą być połączone z tą samą klasą, w której są one praktyczne na podstawie określonych wymagań projektowych. W innych tematach tej sekcji obiekty i interfejsy skojarzone z tymi obiektami zostaną omówione zgodnie z scenariuszem przedstawionym na diagramie.

- Niektóre obiekty są implementowane osobno. Na przykład Kompilowanie projektów i rozwiązań odbywa się w oddzielnych wątkach, a obiekt służący do zarządzania kompilacją działa niezależnie od obiektu opisującego konfigurację kompilacji.

  Aby uzyskać więcej informacji na temat interfejsów obiektów konfiguracji i interfejsów obiektów dostawcy konfiguracji na poprzednim diagramie, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md). Ponadto [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md) zawiera więcej informacji na temat interfejsów programu Configuration Builder i obiektów zależności kompilacji, a także [Konfiguracja projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md) opisuje interfejsy dołączone do programu wdrażania konfiguracji i obiektów zależności wdrożenia. Na koniec [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md) zawiera informacje na temat grup danych wyjściowych i interfejsów obiektów wyjściowych oraz użycie stron właściwości do wyświetlania i ustawiania właściwości zależnych od konfiguracji.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Konfiguracja projektu do kompilowania](../../extensibility/internals/project-configuration-for-building.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
