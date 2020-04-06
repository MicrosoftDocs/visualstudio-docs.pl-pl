---
title: Omówienie opcji konfiguracji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d5ac25fcef7b942b791402baf17982c9810e92a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709408"
---
# <a name="configuration-options-overview"></a>Omówienie opcji konfiguracji
Projekty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] w może obsługiwać wiele konfiguracji, które mogą być budowane, debugowane, uruchamiane i/lub wdrażane. Konfiguracja jest typem kompilacji opisanym z nazwanym zestawem właściwości, zazwyczaj przełącznikami kompilatora i lokalizacjami plików. Domyślnie nowe rozwiązania zawierają dwie konfiguracje: *Debugowanie* i *Zwolnij*. Te konfiguracje mogą być stosowane przy użyciu ustawień domyślnych lub modyfikowane w celu spełnienia określonych wymagań dotyczących rozwiązania i/lub projektu. Niektóre pakiety mogą być budowane na dwa sposoby: jako edytor ActiveX lub jako składnik w miejscu. Projekty nie muszą jednak obsługiwać wielu konfiguracji. Jeśli dostępna jest tylko jedna konfiguracja, ta konfiguracja jest mapowana na wszystkie konfiguracje rozwiązania.

 Konfiguracje zazwyczaj składają się z dwóch części: nazwy konfiguracji (na przykład *debugowania* lub *wydania)* i ustawień platformy. Nazwa platformy konfiguracji identyfikuje środowisko, które jest docelowe konfiguracji, takie jak zestaw interfejsu API lub platforma systemu operacyjnego. Użytkownicy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nie mogą utworzyć platformy; muszą wybrać spośród wyborów, na które pozwala projekt VSPackage. Gdy użytkownik instaluje VSPackage, platformy dostarczania utworzone podczas tworzenia pakietu może powierzchni dowolnej nazwy platformy żądane na podstawie wszelkich kryteriów ustawionych przez twórcę pakietu. Użytkownik może następnie wybrać z listy platform udostępnionych za pośrednictwem VSPackage, gdy strony właściwości są tworzone.

 Nazwy platform są opcjonalne, ponieważ nie wszystkie projekty obsługują koncepcję platform. Gdy konfiguracja nie ma nazwy platformy, ciąg **N/A** jest wyświetlany w interfejsie użytkownika.

 Każde rozwiązanie ma swój własny zestaw konfiguracji, z których tylko jeden może być aktywny w czasie. Konfiguracja rozwiązania to zestaw nie więcej niż jednej konfiguracji z każdego projektu. Zastrzeżenie "nie więcej niż" wynika z opcji wykluczenia projektu z konfiguracji rozwiązania. Użytkownicy mogą tworzyć własne niestandardowe konfiguracje rozwiązań.

 W poniższej tabeli przedstawiono typową konfigurację dla projektu. Wiersze są oznaczone nazwami konfiguracji i kolumnami z nazwami platform.

|Nazwa konfiguracji|Platforma: Win32|Platforma: Win64|
|------------------------|----------------------|----------------------|
|*Debugowanie*|\<Ustawienia debugowania win32>|\<Ustawienia debugowania win64>|
|*Release*|\<Zwolnij> ustawień win32|\<Zwolnij> ustawień win64|
|*MyConfig ( MyConfig )*|Nie dotyczy|\<Ustawienia MyConfig Win64>|

> [!NOTE]
> Nie można utworzyć konfiguracji rozwiązania *MyConfig,* która wyklucza platformę Win32, chyba że kierowany projekt nie obsługuje usługi Win32.

 Zmiana aktywnej konfiguracji rozwiązania wybiera zestaw konfiguracji projektu, który jest budowany, uruchamiany, debugowany lub wdrażany w tym rozwiązaniu. Na przykład jeśli zmienisz konfigurację aktywnego rozwiązania z *Release* na *Debug*, wszystkie projekty w ramach tego rozwiązania są automatycznie tworzone przy konfiguracji projektów wskazanej w konfiguracji debugowania rozwiązania. Konfiguracje projektów są również nazywane *debugowaniem,* chyba że użytkownik dokonał ręcznych zmian w menedżerze konfiguracji środowiska.

 Właściwości konfiguracji rozwiązania przechowywane dla każdego projektu obejmują nazwę projektu, nazwę konfiguracji projektu, flagi wskazujące, czy chcesz skompilować lub wdrożyć, oraz nazwę platformy. Aby uzyskać więcej informacji, zobacz [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md).

 Użytkownik może wyświetlać i ustawiać parametry konfiguracji rozwiązania, wybierając rozwiązanie w hierarchii (Eksplorator rozwiązań) i otwierając strony właściwości. Podobnie można wyświetlać i ustawiać parametry konfiguracji projektu, wybierając projekt w Eksploratorze rozwiązań i otwierając strony właściwości dla tego projektu.

 Użytkownik może również utworzyć jeden projekt przy użyciu ustawień konfiguracji wersji, a cała reszta z ustawieniami konfiguracji debugowania, jeśli to konieczne. Aby uzyskać więcej informacji, zobacz [Konfiguracja projektu do tworzenia](../../extensibility/internals/project-configuration-for-building.md).

 Na poniższym diagramie pokazano, jak interfejsy, które obsługują konfiguracje rozwiązania i projektu są implementowane:

 ![Grafika interfejsu konfiguracyjnego](../../extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces") Interfejsy konfiguracyjne

 Kilka uwag odnoszących się do poprzedniego diagramu:

- `IDispatch`jest oznaczony jako opcjonalny w obiekcie konfiguracji. W szczególności jest opcjonalne, aby interfejsy konfiguracji na obiekcie przeglądania.

- `IVsDebuggableProjectCfg`jest oznaczony jako opcjonalny w obiekcie konfiguracji, ale jest wymagany do obsługi debugowania.

- `IVsProjectCfg2`jest oznaczony jako opcjonalny w obiekcie konfiguracji, ale jest potrzebny do obsługi grupowania danych wyjściowych.

- Obiekt Dostawca konfiguracji jest oznaczony jako obiekt opcjonalny, ale jest to opcja, w której należy go zaimplementować. Obiekt można zaimplementować na obiekcie projektu lub na oddzielnym obiekcie.

- `IVsCfgProvider2`jest potrzebne do obsługi platformy i edycji konfiguracji. `IVsCfgProvider`jest wystarczające, jeśli nie zaimplementujesz tej funkcji.

- Niektóre z tych obiektów pokazanych na diagramie jako oddzielne obiekty mogą być łączone w tej samej klasie, gdzie są praktyczne na podstawie określonych wymagań projektowych. W innych tematach tej sekcji jednak obiekty i interfejsy skojarzone z tymi obiektami zostaną omówione zgodnie ze scenariuszem przedstawionym na diagramie.

- Niektóre obiekty są implementowane oddzielnie. Na przykład tworzenie projektu i rozwiązania występują na oddzielnych wątków i obiektu do zarządzania okresami życia kompilacji oddzielnie od obiektu opisującego konfigurację kompilacji.

  Aby uzyskać więcej informacji na temat interfejsów obiektów konfiguracji i interfejsów obiektów dostawcy konfiguracji na poprzednim diagramie, zobacz [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md). Ponadto [konfiguracja projektu do tworzenia](../../extensibility/internals/project-configuration-for-building.md) zawiera więcej informacji na temat konstruktora konfiguracji i kompilacji interfejsów obiektów zależności i [konfiguracji projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md) dalej opisuje interfejsy dołączone do obiektu zależności wdrażania konfiguracji i wdrożenia. Na koniec [konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md) opisuje interfejsy grupy wyjściowej i obiektów wyjściowych oraz użycie stron właściwości do wyświetlania i ustawiania właściwości zależnych od konfiguracji.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>
- [Konfiguracja projektu do budowy](../../extensibility/internals/project-configuration-for-building.md)
- [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
