---
title: Scenariusze instalacji pakietu VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6bacb7a8226ac9f82987eede32b9df18a103270a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53932947"
---
# <a name="vspackage-setup-scenarios"></a>Scenariusze instalacji pakietu VSPackage

Należy zaprojektować swój Instalatora pakietu VSPackage, aby zapewnić elastyczność. Na przykład może być konieczne w przyszłości wersji poprawki zabezpieczeń lub mogą ulec zmianie strategii biznesowej, która wymaga dokładnego side-by-side obsługą kontroli wersji.

W [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md), możesz przeczytać o korzyści i problemy dotyczące obsługi instalacje side-by-side [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] z udostępnionego lub side-by-side instalacje Twojego pakietu VSPackage. Krótko mówiąc, pakietów VSPackage side-by-side zapewniają większą elastyczność do obsługi nowych funkcji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

Scenariusze omówione w tym temacie nie są tylko wybrane opcje, ale są przedstawione jako sugerowane najlepsze rozwiązanie.

## <a name="components-privacy-and-sharing"></a>Składniki, ochrony prywatności i udostępnianie

### <a name="make-your-components-independent"></a>Uniezależnić składników

Po identyfikować i wypełnić składnika, przypisać `GUID`i wdrożyć składnik, nie można zmienić jego skład. Jeśli zmienisz kompozycji składnika, wynikowy składnika musi być nowego składnika z nową `GUID`. Biorąc pod uwagę następujące fakty, największą elastyczność versioning jest udzielone, wprowadzając jednostki niezależne, samodzielnego każdego składnika. Aby uzyskać więcej informacji na temat zasad regulujących składniki zobacz [zmiany kodu składnika](/windows/desktop/Msi/changing-the-component-code) i [co się stanie, jeśli składnik reguły są uszkodzone?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nie należy mieszać prywatnych i udostępnionych zasobów w składniku

Zliczanie odwołań występuje na poziomie składnika. W związku z tym mieszanie zasobów udostępnionych i prywatnych w jednym składniku uniemożliwia aktualizują zasoby z prywatnych, takich jak plik wykonywalny bez zastępowania także zasoby udostępnione. W tym scenariuszu tworzy problemy ze zgodnością wsteczną i uniemożliwia tworzenie funkcji side-by-side.

Na przykład, wartości rejestru są używane do rejestrowania swojej pakietów VSPackage przy użyciu [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] powinny być przechowywane w składniku oddzielnie od używany do rejestrowania Twojego pakietu VSPackage przy użyciu programu Visual Studio. Wartości rejestru lub plików udostępnionych przejść w jeszcze inny składnik.

## <a name="scenario-1-shared-vspackage"></a>Scenariusz 1: Udostępnione pakietu VSPackage

W tym scenariuszu udostępnionego pakietu VSPackage (pojedynczy plik binarny, który obsługuje wielu wersji programu Visual Studio jest dostarczany w pakiecie Instalatora Windows. Rejestrowanie z każdą wersją programu Visual Studio jest kontrolowana przez funkcje wybierane przez użytkownika. Oznacza to również, że po przypisaniu do oddzielania funkcji, każdego składnika można wybrać indywidualnie celu instalacji lub odinstalowania, zapewnieniem użytkownikowi kontroli nad integrowanie pakietu VSPackage różne wersje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. (Zobacz [funkcje Instalatora Windows](/windows/desktop/Msi/windows-installer-features) Aby uzyskać więcej informacji na temat korzystania z funkcji w pakietów Instalatora Windows.)

![Instalator udostępnionego pakietu VSPackage VS](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak pokazano na ilustracji, składników udostępnionych stają się częścią funkcji Feat_Common, która będzie zawsze instalowana. Przez funkcje Feat_VS2002 i Feat_VS2003 widoczności, użytkownicy mogą wybrać w momencie instalacji w wersjach programu Visual Studio mają pakietu VSPackage, aby zintegrować. Użytkownicy mogą również używać trybu konserwacji Instalatora Windows do dodawania lub usuwania funkcji, która w tym przypadku dodaje lub usuwa informacje o rejestracji pakietu VSPackage z różnych wersji programu Visual Studio.

> [!NOTE]
> Ustawienie funkcji kolumnę wyświetlaną na wartość 0 powoduje ukrycie go. Wartość w kolumnie poziom niski, taką jak 1, gwarantuje, że zawsze zostanie ona zainstalowana. Aby uzyskać więcej informacji, zobacz [właściwość INSTALLLEVEL](/windows/desktop/Msi/installlevel) i [tabeli funkcji](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenariusz 2: Udostępnione aktualizacji pakietu VSPackage

W tym scenariuszu jest dostarczany zaktualizowaną wersję Instalatora pakietu VSPackage w scenariuszu 1. Rozważań aktualizacja dodaje obsługę programu Visual Studio, ale jej może również być prostsze poprawkę zabezpieczeń lub poprawki z dodatkiem service pack. Instalowanie składników nowszej zasady Instalatora Windows wymagają, że niezmienione składniki już w systemie nie są ponownie kopiowane. W takim przypadku system w wersji 1.0 już istnieje zastąpić aktualizowanego składnika Comp_MyVSPackage.dll i Pozwól użytkownikom wybrać, można dodać nowej funkcji Feat_VS2005 za jego pomocą Comp_VS2005_Reg składnika.

> [!CAUTION]
> Zawsze, gdy pakietu VSPackage jest współużytkowana przez wiele wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], istotne jest, że kolejne wersje pakietu VSPackage zachowania zgodności z poprzednimi wersjami z wcześniejszych wersji programu Visual Studio. W przypadku, gdy nie można zachować zgodności z poprzednimi wersjami, należy użyć pakietów VSPackage side-by-side przypadku wartość prywatna. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS udostępnione VS Update pakiet Instalatora](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

W tym scenariuszu przedstawiono nowego Instalatora pakietu VSPackage, korzystając z zalet Instalatora Windows obsługę niewielkie uaktualnienia. Użytkownicy instalują wersji 1.1 i uaktualni ona w wersji 1.0. Jednak nie jest konieczne w wersji 1.0 w systemie. Tym samym Instalator zainstaluje wersji 1.1 w systemie bez wersji 1.0. Zaletą zapewnienie niewielkie uaktualnienia w ten sposób jest to, że nie jest konieczne przechodzą przez prac związanych z tworzeniem uaktualnienia Instalatora i Instalator pełnego produktu. Jeden Instalator wykonuje oba zadania. Poprawkę zabezpieczeń lub service pack może zamiast tego skorzystaj z zalet poprawek Instalatora Windows. Aby uzyskać więcej informacji, zobacz [stosowanie poprawek i uaktualnień](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenariusz 3: Side-by-Side pakietu VSPackage

W tym scenariuszu przedstawiono dwa pliki instalacyjne pakietu VSPackage — jeden dla każdej wersji programu Visual Studio .NET 2003 i programu Visual Studio. Każdy Instalator instaluje side-by-side i prywatnych, pakietu VSPackage (jedna, która jest specjalnie utworzone zainstalowane dla konkretnej wersji programu Visual Studio). Każdego pakietu VSPackage znajduje się w jego własnej składnika. W związku z tym, każdy może być indywidualnie obsługiwany przy użyciu poprawek lub obsługi wersji. Ponieważ biblioteki DLL pakietu VSPackage teraz jest specyficzny dla wersji, jest bezpieczne dołączyć swoje informacje rejestracyjne w jednym składniku jako biblioteki DLL.

![VS Side-by-Side a Package installer](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Instalator, każdy zawiera również kod, który jest współużytkowana przez dwa pliki instalacyjne. Po zainstalowaniu udostępnionego kodu do wspólnej lokalizacji instalacji oba pliki .msi zostanie zainstalowany kod udostępniony tylko raz. Instalator w drugi po prostu zwiększa licznik odwołań do składnika. Licznik odwołań temu, jeśli jeden z pakietów VSPackage zostanie odinstalowany, kod udostępniony pozostanie dla pakietu VSPackage. Drugi pakietu VSPackage odinstalowanie spowoduje także udostępnionego kodu zostaną usunięte.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenariusz 4: Side-by-Side pakietu VSPackage aktualizacji

W tym scenariuszu Twojego pakietu VSPackage dla programu Visual Studio dotknięte luki w zabezpieczeniach, a następnie należy wydać aktualizacji. Tak jak w scenariuszu 2 można utworzyć nowy plik msi, która aktualizuje istniejącą instalację do poprawkę zabezpieczeń, a także wdrażanie nowych instalacji poprawki zabezpieczeń już w miejscu.

W tym przypadku pakietu VSPackage jest zarządzanych pakietu VSPackage, zainstalowane w globalnej pamięci podręcznej zestawów (GAC). Kiedy ponownie kompilujesz hurtownię go, aby uwzględniał poprawki zabezpieczeń, należy zmienić numer poprawki część numeru wersji zestawu. Informacje o rejestracji dla nowego numeru wersji zestawu zastępuje poprzednią wersję, powodując [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] można załadować zestawu stały.

![Instalator Side-by-Side VS pakiet aktualizacji programu VS](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Aby uzyskać więcej informacji na temat wdrażania zestawów side-by-side, zobacz [upraszczanie wdrażania i rozwiązywania piekłem bibliotek DLL, przy użyciu programu .NET Framework](https://msdn.microsoft.com/library/ms973843.aspx).

## <a name="see-also"></a>Zobacz też

[Windows Installer](/windows/desktop/Msi/windows-installer-portal)  
[Obsługiwanie wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)