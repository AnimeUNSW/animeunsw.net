<script>
  import { InfoCard } from "$lib/components/ui/card";
  import * as Accordion from "$lib/components/ui/accordion";
</script>

<svelte:head>
  <title>Info | AnimeUNSW</title>
</svelte:head>

<div
  class="mt-3 flex flex-col items-center space-y-4 px-4 sm:px-8 md:mt-8 md:space-y-8"
>
  <div class="md:w-[640px]">
    <Accordion.Root type="multiple">
      <Accordion.Item value="item-1">
        <Accordion.Trigger>How do I come to events?</Accordion.Trigger>
        <Accordion.Content>
          You can find information about our events on our social media such as
          our Instagram and Discord. A full list of upcoming events can be found
          on our <a
            href="https://campus.hellorubric.com/?s=12432"
            target="_blank"
            class="text-primary underline">Rubric page</a
          >.
        </Accordion.Content>
      </Accordion.Item>
      <Accordion.Item value="item-2">
        <Accordion.Trigger
          >Do I need to be a member to come to events?</Accordion.Trigger
        >
        <Accordion.Content>
          You will need to be a member to join our in-person events, although
          everyone is welcome to join events in the Discord server!
        </Accordion.Content>
      </Accordion.Item>
      <Accordion.Item value="item-3">
        <Accordion.Trigger
          >Do I need to be a member/UNSW student to be verified in the Discord
          server?</Accordion.Trigger
        >
        <Accordion.Content>
          Anyone can be verified to our server as long as you go through the
          verification process correctly. You do not have to be a member to
          participate in server activities!
        </Accordion.Content>
      </Accordion.Item>
      <Accordion.Item value="item-4">
        <Accordion.Trigger>What are the membership benefits?</Accordion.Trigger>
        <Accordion.Content>
          Being a member will allow you to attend all our in-person events while
          also getting membership discounts with some of our sponsors.
        </Accordion.Content>
      </Accordion.Item>
      <Accordion.Item value="item-5">
        <Accordion.Trigger>How do I become a member?</Accordion.Trigger>
        <Accordion.Content>
          To become a member with us, go to our <a
            href="https://campus.hellorubric.com/?tab=memberships&s=12432"
            target="_blank"
            class="text-primary underline">Rubric page</a
          > where you can buy a membership. If you are a UNSW student, please log
          in using SSO.
        </Accordion.Content>
      </Accordion.Item>
      <Accordion.Item value="item-6">
        <Accordion.Trigger
          >I have a grievance with another member! What should I do?</Accordion.Trigger
        >
        <Accordion.Content>
          If there are any grave concerns or complaints, please contact us at
          unswanime@gmail.com.
        </Accordion.Content>
      </Accordion.Item>
    </Accordion.Root>
  </div>

  <h2 class="text-center text-2xl md:text-4xl">Want to contact us?</h2>
  <div class="mb-8 flex flex-wrap justify-center gap-y-4 md:gap-x-8">
    <InfoCard header="General Enquiries"
      >For all general questions and information, please don't hesitate to reach
      out. Simply send an email to <a
        href="mailto:unswanime@gmail.com"
        class="text-primary underline">unswanime@gmail.com</a
      > and we'll get back to you as soon as we can. Alternatively, feel free to
      reach out on any of our socials, which can be found in the top right corner
      of the website under the “Join” header.</InfoCard
    >
    <InfoCard header="Sponsorship Enquiries"
      >Interested in collaborating with AUNSW as a sponsor? We welcome
      partnerships that can enhance the experiences of our anime community.
      Please direct all sponsorship-related queries to our externals director
      Felix at <a
        href="mailto:sponsors@animeunsw.net"
        class="text-primary underline">sponsors@animeunsw.net</a
      >, and let's explore how we can work together.</InfoCard
    >
  </div>
</div>
