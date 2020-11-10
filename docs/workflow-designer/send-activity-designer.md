---
title: Projektant przepływu pracy — Wyślij do projektanta działań
description: Informacje o działaniu wysyłania i sposobach tworzenia i konfigurowania działania wysyłania przy użyciu projektanta działania wysyłania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d78925411f911f9c0dfc0c2cfff891deca0e91e3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434054"
---
# <a name="send-activity-designer"></a>Send, projektant działań

Projektant działań **wysyłania** służy do tworzenia i konfigurowania <xref:System.ServiceModel.Activities.Send> działania.

## <a name="the-send-activity"></a>Wysyłanie działania

 <xref:System.ServiceModel.Activities.Send>Działanie służy do wysyłania komunikatu do usługi. <xref:System.ServiceModel.Activities.ReceiveReply>Działanie może być powiązane z <xref:System.ServiceModel.Activities.Send> działaniem, które odbiera komunikat w ramach wzorca wymiany komunikatów żądania/odpowiedzi na kliencie.

### <a name="using-the-send-activity-designer"></a>Korzystanie z projektanta działań wysyłania

Dostęp do projektanta działania **wysyłania** w kategorii **Obsługa wiadomości** w **przyborniku**. Projektanta działania **wysyłania** można przeciągnąć z **przybornika** i porzucić na Projektant przepływu pracy powierzchnię, wszędzie tam gdzie działania są zwykle umieszczane. Spowoduje to utworzenie <xref:System.ServiceModel.Activities.Send> działania z domyślnym <xref:System.Activities.Activity.DisplayName%2A> wysyłaniem. <xref:System.Activities.Activity.DisplayName%2A>Można edytować w nagłówku projektanta działania **wysyłania** lub w polu **DisplayName** siatki właściwości.

Aby utworzyć <xref:System.ServiceModel.Activities.ReceiveReply> działanie i powiązać je z wybranym <xref:System.ServiceModel.Activities.Send> działaniem, kliknij prawym przyciskiem myszy projektanta działania **wysyłania** , kliknij pozycję **Utwórz ReceiveReply** w menu kontekstowym, a projektant **ReceiveReplyForSend** pojawia się poniżej projektanta **wysyłania** . <xref:System.ServiceModel.Activities.ReceiveReply>Działanie to działanie, które odbiera komunikat w ramach wzorca wymiany komunikatów żądania/odpowiedzi na kliencie. Można go skonfigurować za pomocą narzędzia **ReceiveReplyForSend** Designer.

Alternatywnie, Projektant szablonów **SendAndReceiveReply** w kategorii **Obsługa wiadomości** w **przyborniku** może służyć do tworzenia pary wstępnie skonfigurowanych <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. Aby uzyskać więcej informacji o korzystaniu z szablonów **SendAndReceiveReply** i **ReceiveReplyForSend** , zobacz temat [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .

### <a name="the-send-activity-properties"></a>Właściwości działania wysyłania

W poniższej tabeli przedstawiono <xref:System.ServiceModel.Activities.Send> właściwości i opisano sposób ich użycia w projektancie. Te właściwości można edytować w siatce właściwości lub na Projektant przepływu pracy powierzchni.

| Nazwa właściwości | Wymagany | Użycie |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | Fałsz | Przyjazna nazwa <xref:System.ServiceModel.Activities.Send> działania. Wartość domyślna to Send. Chociaż <xref:System.Activities.Activity.DisplayName%2A> nie jest to ściśle wymagane, najlepszym rozwiązaniem jest użycie jednego z nich. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | Prawda | Nazwa operacji usługi wywołanej przez to <xref:System.ServiceModel.Activities.Send> działanie. Ta właściwość służy do konstruowania wartości domyślnej właściwości **Akcja** , jeśli właściwość **Akcja** nie jest jawnie ustawiona. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | Prawda | Nazwa kontraktu usługi, który ma zostać wywołany przez usługę. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | Fałsz | Określa komunikat lub zawartość parametru do odebrania. Może to być <xref:System.ServiceModel.Activities.ReceiveMessageContent> działanie lub <xref:System.ServiceModel.Activities.ReceiveParametersContent> działanie. Edytuj tę właściwość, wybierając przycisk wielokropka obok pola **zawartość** w siatce właściwości lub klikając przycisk **Definiuj...** obok etykiety **zawartość** na powierzchni projektanta działań **.** Wyświetla okno dialogowe **definicji zawartości** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Definicja zawartości](../workflow-designer/content-definition-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | Fałsz | Określa <xref:System.ServiceModel.Activities.CorrelationHandle> używany do kierowania komunikat do odpowiedniego wystąpienia przepływu pracy.<br /><br /> Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Edytor wyrażeń** . Więcej informacji o użyciu tego okna dialogowego można znaleźć w temacie How to [: Use the Expression Editor](../workflow-designer/how-to-use-the-expression-editor.md) . |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | Fałsz | Określa kolekcję <xref:System.ServiceModel.Activities.CorrelationInitializer> obiektów, które inicjują wiele <xref:System.ServiceModel.Activities.CorrelationHandle> obiektów, które konfigurują to <xref:System.ServiceModel.Activities.Send> działanie w ramach przepływu pracy. Kliknij przycisk wielokropka obok <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> właściwości w siatce właściwości, aby otworzyć okno dialogowe **Dodawanie inicjatorów korelacji** . Aby uzyskać więcej informacji na temat korzystania z tego pola, zobacz [okno dialogowe Dodawanie CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | Fałsz | Kolekcja znanych typów dla operacji usługi, która ma zostać wywołana przez to <xref:System.ServiceModel.Activities.Send> działanie. Ta właściwość powinna być używana w połączeniu z <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> właściwością ustawioną na <xref:System.Runtime.Serialization.DataContractSerializer> . Jest on ignorowany, jeśli <xref:System.Xml.Serialization.XmlSerializer> jest używany.<br /><br /> Wybierz przycisk wielokropka obok pola **KnownTypes** w siatce właściwości, aby wyświetlić okno dialogowe **edytora kolekcji typów** , za pomocą którego można dodać odpowiednie typy.<br /><br /> Wybierz przycisk wielokropka obok pola **KnownTypes** w siatce właściwości, aby wyświetlić okno dialogowe **Edytor kolekcji typów** , w którym można dodać odpowiednie typy. Aby uzyskać więcej informacji na temat używania tego pola, zobacz [okno dialogowe Edytor kolekcji typów](../workflow-designer/type-collection-editor-dialog-box.md) . |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | Prawda | Określa <xref:System.Net.Security.ProtectionLevel> dla wiadomości.<br /><br /> 1.  <xref:System.Net.Security.ProtectionLevel> oznacza tylko uwierzytelnianie.<br />2.  <xref:System.Net.Security.ProtectionLevel> oznacza, że dane podpisywania mają zapewnić integralność przesyłanych danych.<br />3.  <xref:System.Net.Security.ProtectionLevel> oznacza szyfrowanie i podpisywanie danych w celu zapewnienia poufności i integralności przesyłanych danych. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | Prawda | Serializator do użycia dla operacji usługi, która ma zostać wywołana przez <xref:System.ServiceModel.Activities.Send> działanie. Wartość domyślna to <xref:System.Runtime.Serialization.DataContractSerializer> , która serializacji i deserializacji wystąpienia typu do strumienia XML lub dokumentu przy użyciu dostarczonego kontraktu danych. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | Fałsz | Określa nagłówek akcji wiadomości. Jeśli nie jest on jawnie ustawiony, jego wartość domyślna to: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}` . Jeśli określono w <xref:System.ServiceModel.Activities.Send> działaniu, <xref:System.ServiceModel.Activities.Receive> działanie, które odbierze komunikat, musi mieć taką samą wartość, aby komunikat był prawidłowo dostarczany. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | <xref:System.Security.Principal.TokenImpersonationLevel>Dozwolony dla odbiorcy wiadomości. Definiuje on poziomy personifikacji zabezpieczeń, które określają stopień, w jakim proces serwera może działać w imieniu procesu klienta.<xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że poziom personifikacji nie jest przypisany. <xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że proces serwera nie może uzyskać informacji identyfikacyjnych dotyczących klienta i nie może personifikować klienta. <xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że proces serwera może uzyskać informacje o kliencie, takie jak identyfikatory zabezpieczeń i uprawnienia, ale nie może personifikować klienta. Jest to przydatne w przypadku serwerów eksportujących własne obiekty, na przykład produktów bazy danych, które eksportują tabele i widoki. Korzystając z pobranych informacji o zabezpieczeniach klienta, serwer może podejmować decyzje dotyczące weryfikacji dostępu bez możliwości korzystania z innych usług, które korzystają z kontekstu zabezpieczeń klienta. <xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że proces serwera może personifikować kontekst zabezpieczeń klienta w jego systemie lokalnym. Serwer nie może personifikować klienta w systemach zdalnych. <xref:System.Security.Principal.TokenImpersonationLevel> wskazuje, że proces serwera może personifikować kontekst zabezpieczeń klienta w systemach zdalnych. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | To <xref:System.ServiceModel.Endpoint> <xref:System.ServiceModel.Activities.Send> działanie wysyła komunikat do. Jeśli ta właściwość jest ustawiona, <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> Właściwość powinna mieć **wartość null**. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | <xref:System.ServiceModel.EndpointAddress>Do której zostanie wysłany komunikat. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Nazwa konfiguracji punktu końcowego. Ta właściwość jest ustawiana podczas konfigurowania punktu końcowego w pliku konfiguracji. Ta właściwość powinna być ustawiona na nazwę podaną w **\<endpoint>** elemencie w pliku konfiguracji. Jeśli ta właściwość jest ustawiona, <xref:System.ServiceModel.Activities.Send.Endpoint%2A> Właściwość powinna mieć **wartość null**. |

## <a name="see-also"></a>Zobacz też

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Odbieranie](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)