<script>
    const projects = [
        {
            id: 'discord-bot',
            name: 'Discord Youtube Bot',
            description: 'This is a discord bot that will join your channel and will play the audio from the youtube link that you provided. I built this so that I could play music with my friend on Minecraft and on Stardew Valley, until we found out that Discord actually lets other people listen to whatever you are listening on Spotify :) so all this wasn\'t necessary.',
            technologies: ['Python', 'Discord.py'],
            links: [
                {
                    url: 'https://github.com/matchagreen/barista-bot'
                }
            ],
            image: 'discord-bot.jpg',
            alt: 'Matcha drink'
        },
        {
            id: 'connect-4',
            name: 'Connect 4',
            description: 'This is a server-client based Connect 4 game. The server provides the rules of the game, as well as an opponent to the player, while the client serves as an interface where the user can make their moves and see the status of the game. A star is shown at the bottom of the grid to indicate the last movement done for clarity.',
            technologies: ['PHP', 'Dart'],
            links: [
                {
                    url: 'https://github.com/matchagreen/Connect-4-Server',
                    text: 'Server'
                },
                {
                    url: 'https://github.com/matchagreen/Connect-4-Client',
                    text: 'Client'
                }
            ],
            image: 'connect-4.jpg',
            alt: 'Connect 4 game being played on a terminal'
        },
        {
            id: 'can-bus-visualizer',
            name: 'CAN Bus Visualizer',
            description: 'This is a web application written in React and Typescript. It allows an analyst to view information gathered from the CAN Bus of a vehicle. It displays the traffic gathered from the vehicle in a table, and it shows the sensors as nodes on a map (used Reactflow for the diagram). I lead the Front end team responsible for the look and feel of the application, and collaborated with the Backend team to define the API calls.',
            technologies: ['React', 'Typescript'],
            links: [
                {
                    url: 'https://github.com/iarivas/CS4311_CANBusVisualizer_Team_6'
                }
            ],
            image: 'can-bus-visualizer.png',
            alt: 'Screen of a website showing nodes and message data from a CAN Bus'
        },
        {
            id: 'quiz-app',
            name: 'Quiz App',
            description: 'This is a mobile multi-platform app. It obtains a list of questions from the University of Texas at El Paso\'s server. A user can then select a number of random questions to answer and receive a score and feedback at the end. It requires a user to authenticate themselves.',
            technologies: ['Dart', 'Flutter'],
            links: [
                {
                    url: 'https://github.com/matchagreen/quiz_app'
                }
            ],
            image: 'quiz-app.png',
            alt: 'Screenshot of a mobile app where a user is prompted to answer questions on a quiz'
        }
    ];

    const technologies = [
        {
            name: 'Vue.js',
            link: 'https://vuejs.org',
            category: 'frontend',
            usedAtWork: true
        },
        {
            name: 'Groovy',
            link: 'https://groovy-lang.org',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Javascript',
            link: 'https://developer.mozilla.org/en-US/docs/Web/JavaScript',
            category: 'frontend',
            usedAtWork: true
        },
        {
            name: 'Express.js',
            link: 'https://expressjs.com',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Redis',
            link: 'https://redis.io',
            category: 'backend',
            usedAtWork: true
        },
        {
            name: 'Python',
            link: 'https://www.python.org',
            category: 'backend',
            usedAtWork: false
        },
        {
            name: 'FastAPI',
            link: 'https://fastapi.tiangolo.com',
            category: 'backend',
            usedAtWork: false
        },
        {
            name: 'React.js',
            link: 'https://react.dev',
            category: 'frontend',
            usedAtWork: false
        }
    ]

    $: technologiesNotUsedAtWork = technologies.filter(technology => !technology.usedAtWork);
</script>

<div class='app'>
    <div class='main'>
        <div class='main__me'>
            <div class='main__me__card'>
                <div class='main__me__title' id='about-me'>About Me</div>
                <p>
                    My name is Alan Perez, and I am a Software Engineer at Bloomberg. In my day to day, I work with fullstack web development technologies such as:
                </p>
                <ul>
                    {#each technologies.filter(technology => technology.usedAtWork) as technology }
                        <li>
                            <a href={technology.link} target='_blank'>{ technology.name}</a>
                        </li>
                    {/each}
                </ul>
                <p>But I am also familiar with other technologies such as
                {#each technologiesNotUsedAtWork as technology, idx}
                    <a href={ technology.link }>
                        { technology.name }
                    </a>{
                        technologiesNotUsedAtWork.length === idx + 1 ? '' :
                        technologiesNotUsedAtWork.length === idx + 2 ? ' and ' : ', '
                    }
                {/each}
                . I am interested in the opportunity of using technologies like Ruby, React, and Svelte on a.</p>
                <p>I would like to contribute to companies and projects that promote welfare, or otherwise make a positive wholesome impact.</p>
                <p>Please contact me if you are interested in collaborating or chatting.</p>
            </div>
        </div>
        <div class='main__portfolio'>
            <div class='main__portfolio__title'>Portfolio</div>
            {#each projects as project}
                <div class='main__portfolio__project'>
                    <div class='main__portfolio__project__title'>
                        [ { project.name } ]
                    </div>
                    <div class='main__portfolio__project__content'>
                        <div class='main__portfolio__project__content__description'>
                            <div>{ project.description }</div>
                            {#if project.links?.length}
                                <div class='main__portfolio__project__content__description__links' >
                                    <span>Links:</span>
                                    {#each project.links as link, index }
                                        {#if index > 0}
                                            <span>, </span>
                                        {/if}
                                        <a href={link.url} target='_blank'>{link.text ?? 'Repository'}</a>
                                    {/each}
                                </div>
                            {/if}
                        </div>
                        <img
                            class='main__portfolio__project__content__image'
                            src={ project.image }
                            alt={ project.alt }
                        />
                    </div>
                </div>
            {/each}
        </div>
    </div>
</div>


<style lang='scss'>
a {
    color: #e4894b;
    text-decoration: none;
}

.app {
    color: rgb(237, 234, 226);
    background-color: #1c1c1f;
    font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 16px;
    line-height: 24px;
    min-height: max(100vh, 400px);
}

.main {
    min-width: 400px;
    background-image: url('iceland2.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    background-position: center;

    &__me {
        padding: 40px 60px;
        min-height: max(100vh, 400px);

        &__card {
            background-color: #1c1c1fcc;
            padding: 0 30px 10px;
            border-radius: 5px;
        }

        &__title {
            text-align: center;
            font-size: 38px;
            line-height: 40px;
            padding: 21px 0 21px;
        }
    }

    &__portfolio {
        padding: 0 40px;
        background-color: #1c1c1f;

        display: flex;
        flex-direction: column;
        flex-grow: 1;

        &__title {
            font-size: 38px;
            line-height: 40px;
            padding: 21px 0;
            text-align: center;
        }

        &__project {
            &__title {
                font-size: 24px;
                line-height: 28px;
                padding: 21px 0;
                text-align: center;
            }

            &__content {
                padding-top: 10px;
                display: flex;
                justify-content: space-between;
                min-height: 500px;

                &__description {
                    max-width: 600px;
                    padding-right: 50px;

                    &__links {
                        margin-top: 20px;
                    }
                }

                &__image {
                    max-height: 300px;
                    max-width: 400px;
                    object-fit: contain;
                    border-radius: 5px;
                }
            }
        }
    }
}
</style>

