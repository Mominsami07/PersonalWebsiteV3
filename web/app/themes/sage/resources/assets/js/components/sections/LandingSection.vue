<template>
    <section class="landing" id="home">
        <!-- Video -->
        <div class="landing__video-container">
            <video autoplay muted loop class="landing__video-container--video">
                <source :src="video" type="video/mp4" />
            </video>
        </div>
        <!-- Gradient -->
        <div class="landing__video-gradient"></div>
        <!-- Central Elements -->
        <div class="landing__central-elements">
            <div
                v-if="fields.logo"
                class="landing__central-elements--logo"
                :style="{ backgroundImage: `url('${fields.logo}')` }"
                data-aos="zoom-out"
                data-aos-offset="350"
            ></div>
            <h1
                v-if="fields.name"
                class="landing__central-elements--title"
                :class="{ 'mb-8': !fields.slug }"
            >
                {{ fields.name }}
            </h1>
            <h2 v-if="fields.slug" class="landing__central-elements--slug">
                {{ fields.slug }}
                <vue-typer
                    :text="[
                        fields.slug_ending_1,
                        fields.slug_ending_2,
                        fields.slug_ending_3
                    ]"
                    initial-action="erasing"
                    :pre-erase-delay="1800"
                    :erase-delay="70"
                    :pre-type-delay="70"
                    :type-delay="70"
                    erase-style="backspace"
                ></vue-typer>
            </h2>
            <a
                v-if="fields.button_text"
                class="landing__central-elements--button btn btn-ghost"
                href="#projects"
                v-smooth-scroll
                >{{ fields.button_text }}</a
            >
        </div>
        <!-- Section Footer -->
        <p v-if="fields.bottom_text" class="landing__footer">
            {{ fields.bottom_text }}️
        </p>
    </section>
</template>

<script>
import { VueTyper } from "vue-typer";
export default {
    name: "landing-section",
    components: {
        VueTyper
    },
    data() {
        return {
            fields: JSON.parse(this.landing_fields)
        };
    },
    props: {
        video: String,
        landing_fields: String
    }
};
</script>
