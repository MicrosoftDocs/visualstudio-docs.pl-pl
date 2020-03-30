---
title: Projektant przepływu pracy — projektant działań wyślij
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395218"
---
# <a name="send-activity-designer"></a>Send, projektant działań

Projektant działania **Wyślij** służy do tworzenia <xref:System.ServiceModel.Activities.Send> i konfigurowania działania.

## <a name="the-send-activity"></a>Działanie wyślij

 Działanie <xref:System.ServiceModel.Activities.Send> służy do wysyłania wiadomości do usługi. Działanie <xref:System.ServiceModel.Activities.ReceiveReply> może być powiązane <xref:System.ServiceModel.Activities.Send> z działaniem, które odbiera wiadomość jako część wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

### <a name="using-the-send-activity-designer"></a>Korzystanie z Projektanta działań wysyłania

Uzyskaj dostęp do projektanta działań **Wyślij** w kategorii **Wiadomości** **przybornika**. Projektant działania **Wyślij** można przeciągać z **przybornika** i upuszczać na powierzchnię Projektanta przepływu pracy, gdziekolwiek zwykle umieszczane są działania. Spowoduje to <xref:System.ServiceModel.Activities.Send> utworzenie działania <xref:System.Activities.Activity.DisplayName%2A> z domyślnym wyślij. Można edytować w nagłówku projektanta działania **Wyślij** lub w **polu DisplayName** siatki właściwości. <xref:System.Activities.Activity.DisplayName%2A>

Aby utworzyć <xref:System.ServiceModel.Activities.ReceiveReply> działanie i powiązać <xref:System.ServiceModel.Activities.Send> je z wybranym działaniem, kliknij prawym przyciskiem myszy projektanta działań **Wyślij,** kliknij polecenie Utwórz element **ReceiveReply** w menu kontekstowym, a projektant **ReceiveReplyForSend** pojawi się pod projektantem **Wyślij.** Działanie <xref:System.ServiceModel.Activities.ReceiveReply> jest działanie, które odbiera wiadomość jako część wzorca wymiany komunikatu żądania/odpowiedzi na kliencie. Można go skonfigurować za pomocą **receivereplyForSend** projektanta.

Alternatywnie **SendAndReceiveReply** projektant szablonu w kategorii **Wiadomości** **przybornika** może służyć do tworzenia <xref:System.ServiceModel.Activities.Send> pary <xref:System.ServiceModel.Activities.ReceiveReply> wstępnie skonfigurowane i działania. Aby uzyskać więcej informacji na temat korzystania z **SendAndReceiveReply** i **ReceiveReplyForSend** szablonów, zobacz [SendAndReceiveReply tematu.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Właściwości działania wysyłania

W poniższej <xref:System.ServiceModel.Activities.Send> tabeli przedstawiono właściwości i opisano, jak są one używane w projektancie. Właściwości te mogą być edytowane w siatce właściwości lub na powierzchni Projektanta przepływu pracy.

| Nazwa właściwości | Wymagany | Sposób użycia |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Przyjazna nazwa <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to Wyślij. Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest ściśle wymagane, jest najlepszym rozwiązaniem, aby użyć jednego. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Nazwa operacji usługi wywoływana <xref:System.ServiceModel.Activities.Send> przez to działanie. Ta właściwość jest używana do konstruowania wartości domyślnej dla **Action** właściwości, jeśli **Action** właściwość nie jest jawnie ustawiona. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Nazwa umowy serwisowej, którą usługa ma być wywoływana implementuje. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Określa zawartość wiadomości lub parametrów do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, zaznaczając przycisk wielokropka obok pola **Zawartość** w siatce właściwości lub klikając przycisk **Definiuj...** obok etykiety **Zawartość** na powierzchni projektanta działań **Odbierania.** Oba wyświetlają okno dialogowe **Definicja zawartości.** Aby uzyskać więcej informacji na temat używania tego pola, zobacz temat [okna dialogowego Definicja zawartości.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Określa używane <xref:System.ServiceModel.Activities.CorrelationHandle> do kierowania wiadomości do odpowiedniego wystąpienia przepływu pracy.<br /><br /> Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Edytor wyrażeń.** Aby uzyskać więcej informacji na temat korzystania z tego okna dialogowego, zobacz [how to: Use the Expression Editor](../workflow-designer/how-to-use-the-expression-editor.md) temat. |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które <xref:System.ServiceModel.Activities.CorrelationHandle> inicjują <xref:System.ServiceModel.Activities.Send> wiele obiektów, które konfigurują to działanie w przepływie pracy. Kliknij przycisk wielokropka <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> obok właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji.** Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [temat Okno dialogowe Dodawanie correlationInitializers.](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Kolekcja znanych typów dla operacji usługi, która <xref:System.ServiceModel.Activities.Send> ma być wywoływana przez to działanie. Ta właściwość powinna być <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> używana <xref:System.Runtime.Serialization.DataContractSerializer>w połączeniu z właściwością ustawioną na . Jest ignorowany, <xref:System.Xml.Serialization.XmlSerializer> jeśli jest używany.<br /><br /> Wybierz przycisk wielokropka obok pola **Znane typy** w siatce właściwości, aby wyświetlić okno dialogowe **Edytor kolekcji typów,** za pomocą którego można dodać odpowiednie typy.<br /><br /> Wybierz przycisk wielokropka obok pola **Znane typy** w siatce właściwości, aby wyświetlić okno dialogowe **Edytor kolekcji typów,** za pomocą którego można dodać odpowiednie typy. Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz temat [edytora kolekcji typów.](../workflow-designer/type-collection-editor-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Określa <xref:System.Net.Security.ProtectionLevel> komunikat.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> oznacza tylko uwierzytelnianie.<br />2. <xref:System.Net.Security.ProtectionLevel> oznacza podpisywanie danych w celu zapewnienia integralności przesyłanych danych.<br />3. <xref:System.Net.Security.ProtectionLevel> oznacza szyfrowanie i podpisywanie danych w celu zapewnienia poufności i integralności przesyłanych danych. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Serializator do użycia dla operacji usługi, <xref:System.ServiceModel.Activities.Send> które mają być wywoływane przez działanie. Wartością domyślną jest <xref:System.Runtime.Serialization.DataContractSerializer>, która serializuje i deserializuje wystąpienie typu do strumienia XML lub dokumentu przy użyciu dostarczonej umowy danych. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Określa nagłówek akcji wiadomości. Jeśli nie jest jawnie ustawiona, jego `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`wartość domyślnie wynosi: . Jeśli określono <xref:System.ServiceModel.Activities.Send> w działaniu, <xref:System.ServiceModel.Activities.Receive> działanie, które odbiera wiadomość musi mieć taką samą wartość dla wiadomości, które mają być dostarczane poprawnie. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel> Dozwolone dla odbiorcy wiadomości. Definiuje poziomy personifikacji zabezpieczeń, które regulują stopień, w jakim proces serwera może działać w imieniu procesu klienta.<xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że poziom personifikacji nie jest przypisany. <xref:System.Security.Principal.TokenImpersonationLevel>wskazuje, że proces serwera nie może uzyskać informacji identyfikacyjnych o kliencie i nie może personifikować klienta. <xref:System.Security.Principal.TokenImpersonationLevel>wskazuje, że proces serwera może uzyskać informacje o kliencie, takie jak identyfikatory zabezpieczeń i uprawnienia, ale nie może personifikować klienta. Jest to przydatne w przypadku serwerów, które eksportują własne obiekty, na przykład produkty bazy danych, które eksportują tabele i widoki. Korzystając z pobranych informacji o zabezpieczeniach klienta, serwer może podejmować decyzje dotyczące sprawdzania poprawności dostępu bez możliwości korzystania z innych usług, które korzystają z kontekstu zabezpieczeń klienta. <xref:System.Security.Principal.TokenImpersonationLevel>wskazuje, że proces serwera może personifikować kontekst zabezpieczeń klienta w systemie lokalnym. Serwer nie może personifikować klienta w systemach zdalnych. <xref:System.Security.Principal.TokenImpersonationLevel>wskazuje, że proces serwera może personifikować kontekst zabezpieczeń klienta w systemach zdalnych. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Działanie, <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.Activities.Send> do których wysyła wiadomość. Jeśli ta właściwość <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> jest ustawiona właściwość powinna mieć **wartość null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Do <xref:System.ServiceModel.EndpointAddress> którego wysyłana jest wiadomość. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nazwa konfiguracji punktu końcowego. Ta właściwość jest ustawiana podczas konfigurowania punktu końcowego w pliku konfiguracyjnym. Ta właściwość powinna być ustawiona ** \<** na nazwę podaną w punkcie końcowym>element w pliku konfiguracji. Jeśli ta właściwość <xref:System.ServiceModel.Activities.Send.Endpoint%2A> jest ustawiona, właściwość powinna mieć **wartość null**. |

## <a name="see-also"></a>Zobacz też

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)