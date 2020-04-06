---
title: Scenariusze instalacji pakietu VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703971"
---
# <a name="vspackage-setup-scenarios"></a>Scenariusze instalacji pakietu VSPackage

Ważne jest, aby zaprojektować instalatora VSPackage dla elastyczności. Na przykład może być konieczne wydanie poprawki zabezpieczeń w przyszłości lub może zmienić strategię biznesową, która wymaga dokładnej obsługi wersji obok siebie.

W [obsłudze wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)można przeczytać o zaletach i problemach obsługi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalacji side-by-side z instalacji udostępnionych lub side-by-side programu VSPackage. Krótko mówiąc, pakiety VSPackages side-by-side zapewniają największą [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]elastyczność w obsłudze nowych funkcji programu .

Scenariusze omówione w tym temacie nie są tylko wybory, ale są one przedstawione jako sugerowane najlepsze rozwiązania.

## <a name="components-privacy-and-sharing"></a>Składniki, prywatność i udostępnianie

### <a name="make-your-components-independent"></a>Uazaj swoje komponenty w niezależności

Po zidentyfikowaniu i wypełnieniu komponentu, przypisaniu elementu `GUID`i wdrożeniu składnika nie można zmienić jego składu. Jeśli zmienisz skład komponentu, wynikowy komponent musi być nowym `GUID`komponentem z nowym . Biorąc pod uwagę te fakty, największą elastyczność wersji jest zapewniona przez uczynienie każdego komponentu niezależnym, samowystarczalnym urządzeniem. Aby uzyskać więcej informacji na temat reguł dotyczących składników, zobacz [Zmienianie kodu składnika](/windows/desktop/Msi/changing-the-component-code) i [co się stanie, jeśli reguły składników są łamane?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nie mieszaj zasobów udostępnionych i prywatnych w składniku

Zliczanie odwołań występuje na poziomie komponentu. W związku z tym mieszanie zasobów udostępnionych i prywatnych w jednym składniku uniemożliwia aktualizowanie zasobów prywatnych, takich jak plik wykonywalny, bez zastępowania zasobów udostępnionych. W tym scenariuszu tworzy problemy ze zgodnością z powrotem i ogranicza tworzenie możliwości side-by-side.

Na przykład wartości rejestru używane do rejestrowania [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] vsPackage z powinny być przechowywane w składniku oddzielnie od jednego używanego do rejestrowania VSPackage z programem Visual Studio. Udostępnione pliki lub wartości rejestru są w jeszcze innym składniku.

## <a name="scenario-1-shared-vspackage"></a>Scenariusz 1: Udostępniony pakiet VSPackage

W tym scenariuszu udostępnioneGO VSPackage (pojedynczy plik binarny, który obsługuje wiele wersji programu Visual Studio jest dostarczany w pakiecie Instalatora Windows. Rejestrowanie się w każdej wersji programu Visual Studio jest kontrolowane przez funkcje wybierane przez użytkownika. Oznacza to również, że po przypisaniu do oddzielnych funkcji, każdy składnik może być wybrany indywidualnie do instalacji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]lub dezinstalacji, dzięki czemu użytkownik ma kontrolę nad integracją VSPackage z różnymi wersjami programu . (Zobacz [Funkcje Instalatora Windows, aby](/windows/desktop/Msi/windows-installer-features) uzyskać więcej informacji na temat korzystania z funkcji w pakietach Instalatora Windows).

![Instalator udostępniony vspakage usługi VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak pokazano na ilustracji, udostępnione komponenty są częścią funkcji Feat_Common, która jest zawsze instalowana. Dzięki temu Feat_VS2002 i Feat_VS2003 funkcji są widoczne, użytkownicy mogą wybrać w czasie instalacji, w których wersjach programu Visual Studio mają zintegrować program VSPackage. Użytkownicy mogą również użyć trybu konserwacji Instalatora Windows, aby dodać lub usunąć funkcje, które w tym przypadku dodaje lub usuwa informacje rejestracyjne VSPackage z różnych wersji programu Visual Studio.

> [!NOTE]
> Ustawienie kolumny Ekran obiektu na 0 powoduje ukrycie jej. Wartość kolumny niskiego poziomu, na przykład 1, zapewnia, że zawsze będzie zainstalowana. Aby uzyskać więcej informacji, zobacz [Właściwość INSTALLLEVEL](/windows/desktop/Msi/installlevel) i [tabela funkcji](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenariusz 2: Udostępniona aktualizacja pakietu VSPackage

W tym scenariuszu zostanie dostarczona zaktualizowana wersja instalatora VSPackage w scenariuszu 1. Ze względu na dyskusję aktualizacja dodaje obsługę programu Visual Studio, ale może to być również prostsza poprawka zabezpieczeń lub dodatek Service Pack do naprawienia błędu. Reguły Instalatora Windows dotyczące instalowania nowszych składników wymagają, aby niezmienione składniki już w systemie nie były kopiowane ponownie. W takim przypadku system z wersją 1.0 już obecny zastąpi zaktualizowany składnik Comp_MyVSPackage.dll i pozwoli użytkownikom wybrać, aby dodać nową funkcję Feat_VS2005 z jego Comp_VS2005_Reg składnika.

> [!CAUTION]
> Ilekroć VSPackage jest współużytkowana przez wiele wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]programu , istotne jest, aby kolejne wersje programu VSPackage utrzymywały zgodność z poprzednimi wersjami programu Visual Studio. W przypadku, gdy nie można zachować zgodności z powrotem, należy użyć obok siebie, prywatne VSPackages. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![Instalator aktualizacji pakietu udostępnionego vs vs](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

W tym scenariuszu przedstawiono nowy instalator VSPackage, korzystając z obsługi Instalatora Windows dla uaktualnień pomocniczych. Użytkownicy po prostu zainstalować wersję 1.1 i uaktualnia wersję 1.0. Nie jest jednak konieczne, aby mieć wersję 1.0 w systemie. Ten sam instalator zainstaluje wersję 1.1 w systemie bez wersji 1.0. Zaletą zapewnienia drobnych uaktualnień w ten sposób jest to, że nie jest konieczne, aby przejść przez prace nad opracowaniem instalatora uaktualnienia i instalatora pełnego produktu. Jeden instalator wykonuje oba zadania. Zamiast tego poprawka zabezpieczeń lub dodatek Service Pack mogą korzystać z poprawek Instalatora Windows. Aby uzyskać więcej informacji, zobacz [Łaty i uaktualnienia](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenariusz 3: Pakiet VS-side-by-side

W tym scenariuszu przedstawiono dwa instalatory VSPackage — po jednym dla każdej wersji programu Visual Studio .NET 2003 i Visual Studio. Każdy instalator instaluje obok siebie lub prywatny, VSPackage (który jest specjalnie zbudowany i zainstalowany dla określonej wersji programu Visual Studio). Każdy VSPackage jest w swoim własnym składniku. W związku z tym każdy może być indywidualnie serwisował za pomocą poprawek lub wersji konserwacji. Ponieważ biblioteka DLL vspackage jest teraz specyficzne dla wersji, jest bezpieczne, aby dołączyć jego informacje rejestracyjne w tym samym składniku co biblioteka DLL.

![Instalator pakietu VS Side-by-Side VS](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Każdy instalator zawiera również kod, który jest współużytkowany przez dwóch instalatorów. Jeśli udostępniony kod jest zainstalowany we wspólnej lokalizacji, zainstalowanie obu plików msi zainstaluje udostępniony kod tylko raz. Drugi instalator tylko zwiększa liczbę odwołań na składniku. Liczba odwołań zapewnia, że jeśli jeden z VSPackages zostanie odinstalowany, udostępniony kod pozostanie dla innych VSPackage. Jeśli drugi VSPackage zostanie również odinstalowany, udostępniony kod zostanie usunięty.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenariusz 4: Aktualizacja VSPackage side-by-side

W tym scenariuszu vspackage dla programu Visual Studio ucierpiał na lukę w zabezpieczeniach i trzeba wydać aktualizację. Podobnie jak w scenariuszu 2, można utworzyć nowy plik msi, który aktualizuje istniejącą instalację, aby uwzględnić poprawkę zabezpieczeń, a także wdrożyć nowe instalacje z już istniejącą poprawką zabezpieczeń.

W takim przypadku VSPackage jest zarządzany vspackage zainstalowany w globalnej pamięci podręcznej zestawu (GAC). Podczas przebudowy, aby uwzględnić poprawkę zabezpieczeń, należy zmienić część numeru wersji asfekcyjną numeru wersji zestawu. Informacje o rejestracji dla nowego numeru wersji zestawu zastępuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poprzednią wersję, powodując załadowanie stałego zestawu.

![Instalator aktualizacji pakietu VS Side-by-Side VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Aby uzyskać więcej informacji na temat wdrażania zestawów side-by-side, zobacz [Upraszczanie wdrażania i rozwiązywania piekła biblioteki DLL za pomocą programu .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Zobacz też

- [Instalator Windows](/windows/desktop/Msi/windows-installer-portal)
- [Obsługiwanie wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
