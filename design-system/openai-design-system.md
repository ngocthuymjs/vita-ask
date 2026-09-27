# OpenAI Design System - cho project Vita Ask chatbot

Nguồn chính thức (đã ingest về đây ngày 2026-09-27):
- Figma: Apps in ChatGPT · OpenAI Official (Community) - https://www.figma.com/community/file/1625636989296445101/ (đã mở trong Chrome thuyielts80)
- Docs: https://developers.openai.com/apps-sdk/concepts/ui-guidelines
- Code gốc: https://github.com/openai/apps-sdk-ui (MIT) - toàn bộ tokens CSS đã lưu trong thư mục này
- Storybook: https://openai.github.io/apps-sdk-ui/

## 1. Font (Typography)

**Nguyên tắc OpenAI: KHÔNG dùng custom font. Luôn inherit system font.**
- iOS: SF Pro, Android: Roboto / sans-serif, Web: system stack
- Stack chuẩn trong code:
```
--font-sans: ui-sans-serif, -apple-system, system-ui, "Segoe UI", "Noto Sans", "Helvetica", Arial, sans-serif
```
- OpenAI Sans (font brand cho logo/wordmark) có 5 weights Light/Regular/Medium/Semibold/Bold - chỉ dùng cho brand, KHÔNG dùng cho UI chatbot.
- Weight: normal 400, medium 500, semibold 600 (dùng semibold thay cho bold), bold 700

**Scale (đã lưu full trong openai-variables-primitive.css + Typography.mdx):**
- heading-5xl: 72px/72px/600, 4xl: 60/60/600, 3xl: 48/48/600, 2xl: 36/42/600, xl: 32/38/600, lg: 24/28/600, md: 20/26/600, sm: 18/26/600, xs: 16/24/600
- text-lg: 18/29/400, text-md: 16/24/400 (body chuẩn), text-sm: 14/20/400 (body-small), text-xs: 12/18/400 tracking-wide, text-2xs: 10/14/400, text-3xs: 8/12/400
- Quy tắc chatbot: ưu tiên body + body-small, hạn chế đổi size. Bold/italic/highlight chỉ trong content, không cho structural UI.

## 2. Size, Spacing, Radius

- Control height: 3xs 22px, 2xs 24px, xs 26px, sm 28px, md 32px, lg 36px, xl 40px, 2xl 44px, 3xl 48px
- Gutter: 2xs 6px, xs 8px, sm 10px, md 12px, lg 14px, xl 16px
- Icon: xs 14px, sm 16px, md 18px, lg 20px, xl 22px, 2xl 24px
- Radius: 2xs 2px, xs 4px, sm 6px, md 8px, lg 10px, xl 12px, 2xl 16px, 3xl 20px, 4xl 24px (composer dùng 24px), full 9999px
- Chat: max-width 800px, gutter spacing(5), thread-gutter spacing(4), composer-gutter spacing(3)
- Card: rounded-2xl (16px), border border-default, p-4, shadow-lg
- Không nested scrolling trong card, không edge-to-edge text, giữ padding đều.
- Shadow: 100/200/300/400 + hairline 1px (0.5px trên retina), elevation-geo riêng light/dark.

## 3. Color

**Nguyên tắc: dùng system colors cho text/icon/divider. Brand accent chỉ cho button/badge/icon, không đổi nền text-area, không gradient tự chế.**

File gốc: openai-variables-primitive.css (gray + 7 màu) + openai-variables-semantic.css + openai-tailwind-utilities.css

- Gray (light/dark tự đảo bằng light-dark): 0 #ffffff/#0d0d0d, 25 #fcfcfc/#101010, 50 #f9f9f9/#131313, 75 #f3f3f3/#161616, 100 #ededed/#181818, 150 #dfdfdf/#1c1c1c, 200 #cdcdcd/#212121 ... 900 #181818/#ededed, 1000 #0d0d0d/#ffffff
- Surface: surface #fff/#0d0d0d, secondary, tertiary, elevated, elevated-secondary
- Text: text=gray-1000, secondary=gray-500/700, tertiary=gray-400/600, inverse=gray-0
- Palette full: green #00a240, red #e02e2a, pink #e04c91, orange #e25507, yellow #ffc300, purple #8046d9, blue #0169cc / #0285ff (link primary light #0169cc dark #339cff, hover #013566)
- Semantic: primary (gray-900 solid), secondary, info (blue), success (green), warning (orange), danger/caution (orange/red), discovery (purple) - mỗi loại có soft/solid/outline/ghost/surface + hover/active
- Button primary = gray-900 solid, text inverse. Brand accent chỉ cho primary button trong app.
- User message: light alpha-05, dark alpha-08. Composer bg = surface-elevated.
- Dark mode: dùng [data-theme=dark], color-scheme dark, shadow alpha cao hơn.

## 4. Component (29 components - từ @openai/apps-sdk-ui)

Alert, AppsSDKUIProvider, Avatar (+AvatarGroup), Badge, Button (+ButtonLink), Checkbox, CodeBlock, DatePicker, DateRangePicker, EmptyMessage, Icon, Image, Indicator, Input, Markdown, Menu, Popover, RadioGroup, SegmentedControl, Select, SelectControl, ShimmerText, Slider, Switch, TagInput, TextLink, Textarea, Tooltip, Transition (+AnimateLayout, TransitionGroup)

Tokens component trong openai-variables-components.css:
- Button gap 3/4/6px, font-weight medium 500
- Input gap 4/6/8/10px, border outline alpha-16, focus alpha-50, invalid red-500/600
- Badge sm 20px/md 22px/lg 24px, radius 4/4/6px, font semibold
- Composer radius 24px, chat-max-width 800px
- Dialog min 250 max 450px, padding spacing(5), backdrop black 30%/50%
- Menu radius 12px, item padding, switch 32x19px, slider, segmented-control...

Ví dụ chuẩn OpenAI (ReservationCard): div max-w-sm rounded-2xl border-default bg-surface shadow-lg p-4 + Badge success + Button soft/primary.

## 5. Icon

- Style: monochromatic, outlined, 14-24px. Không nhét logo vào response (ChatGPT tự append logo + app name).
- Bộ Icon trong package: Calendar, Invoice, Maps, Members, Phone... + full set trong src/components/Icon/svg (xem Icons.mdx)
- Dùng: `<Calendar className="size-4" />` (16px)
- Ảnh phải đúng aspect ratio enforced, có alt text, contrast WCAG AA, hỗ trợ resize text.

## 6. Cách apply cho Vita Ask chatbot sau này

1. Cài package (khi làm React):
```
npm install @openai/apps-sdk-ui
@import "tailwindcss";
@import "@openai/apps-sdk-ui/css";
@source "../node_modules/@openai/apps-sdk-ui";
```
2. Hiện tại (spec-v1.html prototype): copy biến cần thiết từ openai-variables-primitive.css vào `<style>` :root, dùng font-sans system, body 16/24, small 14/20, heading semibold, radius 12/16/24, màu gray + blue link.
3. Display modes phải theo: Inline card (tối đa 2 actions, 1 primary CTA + 1 secondary, không tabs/drill-in, không scroll trong), Inline carousel 3-8 items (mỗi item 1 CTA), Fullscreen cho map/editor/list dài (giữ composer), PiP cho game/video/live.
4. Không dùng custom font, không gradient nền text, không đổi màu text core.

Toàn bộ CSS gốc đã lưu: openai-base.css, openai-globals.css, openai-index.css, openai-variables-*.css, openai-tailwind-utilities.css + mdx docs.
